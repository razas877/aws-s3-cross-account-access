# AWS S3 Cross-Account Access

In this project, I created an **Amazon S3 bucket** in one AWS account and granted **another AWS account** permissions to add, modify, and delete objects in the bucket.

---

**This project demonstrates:**
- Creating an S3 bucket
- Configuring **cross-account access** using **S3 Bucket Policy**
- Allowing another AWS account to **read, write, and delete objects**
- Testing permissions from the second AWS account

---

**Steps to Implement**

### 1. Create S3 Bucket
- Go to **AWS S3 Console** → Create Bucket
- Choose a unique bucket name  
- Region: your preferred AWS region
- Block Public Access: **Keep Enabled** (for security)

### 2. Get Target AWS Account ID
- From the second AWS account (the one that needs access), get the **AWS Account ID**.

### 3. Add Bucket Policy
Go to **S3 → Your Bucket → Permissions → Bucket Policy** and add:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowAccountBFullAccess",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::924210591737:root"
            },
            "Action": [
                "s3:*",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::razas877bucket",
                "arn:aws:s3:::razas877bucket/*"
]
        },
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::razas877bucket/*"
        }
    ]
}
  ]
}

**4. Test from Another AWS Account**

From the second AWS account:

Upload a file to the bucket

List files in the bucket

Modify or delete files


**Outcome**

The second AWS account can successfully add, update, and delete objects in the S3 bucket.

Access is controlled securely using IAM & Bucket Policies.
