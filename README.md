# websitelaunchAWS
Launching a website on AWS
## Credits
- Thank you to TechWithLucy

## Services/ Tools Used:
- Amazon S3
- Amazon Route 53
- Amazon S3 

# Cost
- $3 for domain



## Initial Steps to Hosting Website with Custom Domain

- Set up a custom domain name using Amazon Route 53:  can use Amazon Route 53, a domain name system (DNS) service provided by Amazon Web Services, to create a unique and personalized domain name for  website. This allows  to have a web address that reflects  brand or purpose.

- Host  website on an Amazon S3 Bucket: To make  website accessible on the internet,  can use an Amazon S3 Bucket, a scalable and cost-effective storage service. By storing  website's files in an S3 Bucket,  ensure that they are securely stored and easily retrievable.

- Enable static website hosting and link the domain to the S3 bucket: Once  website files are stored in the S3 Bucket,  can enable static website hosting for the bucket. This feature allows  to serve  website's content directly from the S3 Bucket, and can then configure Amazon Route 53 to route traffic from  custom domain to the S3 Bucket, making  website accessible under  chosen domain name.

![alt text](https://lucid.app/publicSegments/view/36be42fc-a4ea-49c9-8f7b-c6dd5101ca2a/image.jpeg)

## Route 53 Domain

- Navigate to Route 53 in AWS by using the search

- Press Register Domain and check desired domain availability. I used ryanonacloud.click and it was available.
![alt text](images/Domain.png)

- Selected the domain and completed Pricing and Contact information. I turned off autorenew and set it up for 1 year. The Top level Domain(TLD) was the cheapest option for this project ".click" For the domain to fully register, this took about 15 minutes under this top level domain. 

## S3 Bucket setup
- Navigate to S3 and create a bucket. name the bucket after the domain that was created. I chose the region US East (N. Virginia) us-east-1 for less latency. Uncheck Block all Public Access so the bucket is accessible by others. Everything else I left default.

![alt text](images/S3bucket.png)

- Navigate into bucket and then uploaded index.html file.

- Properties and then Enable Static website hosting 
![alt text](images/static.png)

- Added a Bucket Policy under permissions. Template below for the bucket policy. Change the [Bucket-Name] to the bucket name created.

```js
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
} 
```

## Route 53 Using Domain to load website
- Route 53 - Under Hosted Zones - View the details of the domain and create record. I switched to the wizard and used the Simple Routing Policy. 

![alt text](images/static.png)

## Result Sample Website

- Go to ryanonacloud.click to see the project example website.

![alt text](images/result.png)



