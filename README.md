# aws-saac03-notes
I am currently working through sample exams from Stephane Maarek’s Udemy course to prepare for AWS certification. After reviewing my incorrect answers, I take detailed notes to reinforce the concepts and ensure I understand the material more thoroughly.

# ACM:
- store/import private HTTPS certificates
- **CAN NOT** generate private certificates, BUT **CAN** generate public certificates.
- Rotate certificates → EventBridge to send notification → rotate certificates manually
- can use **IAM certificate store to store SSL too.**

# ALB:
- create a listener rule to redirect HTTP to HTTPs, if HTTP 80 already exists → only modify it

# AWS Fargate:
- No provisioning, monitoring underlying infrastructure is needed
- Ephemeral storage: 20GB

# AWS Secret Manager:
- store RDS credentials, auto rotate on a regular basis. 0.40$ per secret / month

# AWS Systems Manager Parameter Store:
- store secrets but not auto rotate. 10,000 free parameters.
- ⇒ cost-effective ⇒ **AWS Systems Manager Parameter Store** but **no frequent-rotation**

# AWS Shield and AWS WAF:
- **AWS Shield:** protects against **DDoS attack** on layer 3/4 network. Integrate with CloudFront, Route53, ALB
- **AWS WAF:** protects against **SQL injection, XSS** on layer 7. Filtering malicious HTTP traffic. Integrates with CloudFront, ALB, API Gateway, and AppSync

# AWS Control Tower vs AWS SCPs:
- Use **AWS Control Tower** when you want an **easy, automated way** to set up a governed multi-account environment based on AWS best practices.
- Use **SCPs** when you need **fine-grained control** over permissions and actions across your AWS accounts, ensuring compliance with security policies.

# Cloud Trail:
- Audit actions taken by user, role, services via CLI, Console, APIs, SDK. ⇒ **Event history**

# CloudFront:
- not compatible with DynamoDB
- control permission to S3 → **OAI**

# CloudWatch:
- Region scoped
- CloudWatch needs installing CloudWatch Agent for memory and disk metrics.
- **AWS PHD** (personal health dashboard) offers real-time, account-specific notifications and remediation steps.
- **AWS SHD (service health dashboard)** is a public-facing dashboard providing global service status.

# Comprehend:
- text to insights, heal information

# Cost Explorer:
- Find the root cause of billing, estimate, and predict the price.

# Direct Connect:
- best way to connect on-premises → AWS.

# DocumentDB:
- if migrating MongoDB to it ⇒ **with MongoDB compatibility**

# DynamoDB:
- RPO RTO ⇒ enable point-in-time recovery
- unpredictable traffic ⇒ on-demand capacity mode

# EBS:
- **Magnetic volumes** provide the lowest cost per gigabyte of all EBS volume types

# EC2:
- when stop/start ⇒ data in instance-store will be lost, underlying host can change
- subsequent request fails → increase vCPU-on-demand limit per region (default 20)
- prevent instance-storage from loss when instance terminates → set **DeleteOnTermination = False**
- cannot enable/disable hibernation mode when instance is launched
- **change type in ASG** → create new version of launch template because **launch template is immutable**

# ECS & EKS:
- ECS for containers, EKS for Kubernetes containers

# EFS & FSX:
- EFS for Linux, FSx for Windows, FSx for Lustre
- Sync windows file server on-prem to AWS ⇒ FSx File Gateway

# License Manager:
- when mentioned licenses.

# IAM:
- IAM group should be provided with a policy, not a role

# Kinesis:
- Kinesis Data Stream → real-time
- Stream → **none of the messages are lost, no duplicates are produced, keep order.**
- Kinesis Data Firehose → near real-time

# RDS:
- Increase disk without performance degradation ⇒ change RDS instance settings ⇒ auto storage scaling.

# Redshift:
- **OLAP** database based on PostgreSQL
- Faster than Athena
- Lead node plans queries and sends to compute nodes then lead node aggregates the data
- Import data from EC2 apps, S3 via copy, Kinesis Firehose
- **Redshift Spectrum** helps to query data directly from S3.
- Disaster recovery → **Cross-Region Snapshots**

# Rekognition:
- detect images, videos using machine learning

# S3:
- **S3 Standard**: Immediate
- **S3 Intelligent-Tiering**: Immediate
- **S3 Standard-IA**: Immediate
- **S3 One Zone-IA**: Immediate
- **S3 Glacier**: Minutes to Hours
- **S3 Glacier Deep Archive**: Up to 12 Hours → only **1 or 2 times a year.**
- **CORS** allowing resources in your bucket to be accessed by web applications from different domains
- Object lock: **governance mode** is more flexible than **compliance mode**
- To reduce cost when sharing data to others ⇒ requester pay
- To reduce cost transfer from VPC → S3 use
- From Glacier ⇒ required data in **under 15 minutes** ⇒ **Expedited Retrieval & Purchase provisioned retrieval capacity**
- Bulk Retrieval ⇒ **5 - 12 hrs**
- **SSE-S3 →** cannot modify built-in rotation.
- should not store SSL certificates here

# SQS:
- duplicated consumed messages ⇒ increase the visibility time out **ChangeMessageVisibility**
- **AWS Step Functions** may replace SQS to tackle **duplicated messages problem**

# Snowball:
- use when big data & mentioned on-premises

# Textract:
- extract text from PDFs, JPEG

# VPC:
- instance has no DNS hostname -> enable **DNS Resolution & DNS Hostname VPC configuration**
- Connect VPCs via peering connection
- All subnets can communicate, use security groups to control connections
- Cannot peering A → B → C. Should peering direct from A → C

# AWS Transit Gateway:
- connect on-premises & all VPCs to a single gateway
