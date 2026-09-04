# aws-saa-c03-hands-on-journey
# ☁️ AWS Solutions Architect Associate — Learning Journey

![AWS](https://img.shields.io/badge/AWS-Solutions%20Architect-FF9900?style=for-the-badge\&logo=amazonaws\&logoColor=white)
![Status](https://img.shields.io/badge/Status-In%20Progress-blue?style=for-the-badge)
![Exam](https://img.shields.io/badge/Exam-SAA--C03-orange?style=for-the-badge)

## 🚀 My AWS Learning Journey

I am currently preparing for the **AWS Certified Solutions Architect – Associate (SAA-C03)** certification.

My approach is focused on developing practical AWS skills alongside certification knowledge. Instead of only studying theory, I am using the **AWS Management Console** to deploy resources, configure services, troubleshoot problems, and understand how different AWS services work together.

This repository documents what I have learned and practiced so far.

---

# 📚 AWS Services Covered So Far

## 🖥️ 1. Amazon EC2 — Elastic Compute Cloud

I learned how AWS provides scalable virtual servers through Amazon EC2 and practiced launching and managing EC2 instances.

### Topics Covered

* EC2 instance creation
* Amazon Machine Images (AMI)
* Instance types
* Key pairs
* Public and private IP addresses
* Security Groups
* Inbound and outbound rules
* User Data
* EC2 instance states
* Stop / Start / Reboot / Terminate
* Elastic IP concepts
* EC2 purchasing options
* On-Demand Instances
* Reserved Instances
* Savings Plans concepts
* Spot Instances

### 🧪 Hands-On Practice

## 🧪 Hands-On AWS Architecture Labs

| Lab | AWS Services | Description | Status |
|---|---|---|---|
|[Lab-01](./labs-01/) | EC2, EBS, IAM | EC2 web server with additional EBS storage and IAM role | ✅ Completed |
| Lab 02 – Load Balanced Web App | EC2, ALB | Two EC2 instances behind an Application Load Balancer | 🔄 Next |
| Lab 03 – Auto Scaling | EC2, ALB, ASG | Highly available and scalable web application | ⏳ Planned |
| Lab 04 – Shared Storage | EC2, EFS | Multiple EC2 instances using shared storage | ⏳ Planned |
| Lab 05 – Database Architecture | EC2, ALB, RDS | Highly available application with database | ⏳ Planned |
✔️ Launched EC2 instances through AWS Console
✔️ Configured Security Groups
✔️ Configured HTTP access
✔️ Connected to EC2
✔️ Installed a web server
✔️ Modified inbound rules
✔️ Tested access through EC2 public IP

### 💡 Key Learning

EC2 provides the **compute layer** of an AWS architecture, while services such as Auto Scaling, Elastic Load Balancing, IAM and EBS can be combined with EC2 to create scalable, secure and highly available solutions.

---

# 🔐 2. AWS Identity and Access Management — IAM

IAM has been one of the most important security services in my AWS studies.

### Topics Covered

* IAM Users
* IAM User Groups
* IAM Roles
* IAM Policies
* AWS managed policies
* Customer managed policies
* Inline policies
* JSON policy structure
* Allow and Deny statements
* Principle of Least Privilege
* Multi-Factor Authentication
* Access Keys
* AWS account security concepts

### IAM Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "service:Action",
      "Resource": "*"
    }
  ]
}
```

### 💡 Key Learning

AWS permissions should follow the:

> 🔐 **Principle of Least Privilege**

Users and services should receive **only the permissions they actually require**.

I also learned why IAM Roles are generally preferred over storing long-term AWS credentials on applications or EC2 instances.

---

# 💾 3. Amazon EBS — Elastic Block Store

I studied how EBS provides persistent block storage for EC2 instances.

### Topics Covered

* EBS Volumes
* Root volumes
* Additional volumes
* EBS volume types
* General Purpose SSD
* Provisioned IOPS SSD
* HDD-based volumes
* EBS Snapshots
* Volume resizing
* Attaching and detaching volumes
* Availability Zone relationship

### 🧪 Hands-On Practice

✔️ Created EBS volumes
✔️ Attached storage to EC2
✔️ Identified attached disks from Linux
✔️ Created file systems
✔️ Mounted volumes
✔️ Tested persistent storage

### 💡 Key Learning

An important architectural concept:

```text
EC2 Instance
     │
     ▼
 EBS Volume
     │
     ▼
Availability Zone
```

EBS volumes are **Availability Zone specific**.

Snapshots can be used for backup and to create volumes in other Availability Zones or Regions where required.

---

# 📁 4. Amazon EFS — Elastic File System

I studied EFS as AWS managed shared file storage.

### Topics Covered

* Shared file systems
* NFS
* Linux workloads
* Multiple EC2 access
* Regional availability
* Scalability
* EFS performance concepts
* EFS vs EBS

### 💡 EBS vs EFS

```text
EBS

EC2 ───── EBS
       Block Storage


EFS

EC2-A ─┐
       ├──── EFS
EC2-B ─┘
       Shared File Storage
```

### Key Learning

**EBS** is generally used as block storage for EC2.

**EFS** allows multiple Linux EC2 instances to access a shared file system, making it useful for distributed and highly available applications.

---

# ⚖️ 5. Elastic Load Balancing

I studied how AWS distributes incoming traffic between multiple backend resources.

### Topics Covered

* Elastic Load Balancing
* Application Load Balancer — ALB
* Network Load Balancer — NLB
* Gateway Load Balancer concepts
* Listeners
* Target Groups
* Health Checks
* HTTP/HTTPS traffic
* Layer 7 vs Layer 4 load balancing

### Architecture Concept

```text
                    Users
                      │
                      ▼
             Application Load
                 Balancer
                      │
              Target Group
                 /       \
                /         \
               ▼           ▼
             EC2-1       EC2-2
```

### 💡 Key Learning

Load Balancers improve:

✔️ Availability
✔️ Fault tolerance
✔️ Scalability
✔️ Traffic distribution

Health checks ensure traffic is sent only to healthy targets.

---

# 📈 6. EC2 Auto Scaling

I learned how AWS can automatically adjust EC2 capacity based on application requirements.

### Topics Covered

* Auto Scaling Groups
* Launch Templates
* Minimum capacity
* Desired capacity
* Maximum capacity
* Scaling policies
* Target tracking
* Health checks
* EC2 replacement
* Integration with Load Balancers

### Architecture

```text
                    ALB
                     │
                     ▼
               Target Group
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
        EC2-1      EC2-2      EC2-3
          \          │          /
           \         │         /
             Auto Scaling Group
```

### 💡 Key Learning

Auto Scaling provides two major architectural benefits:

**High Availability** — unhealthy instances can be replaced.

**Elasticity** — compute capacity can increase or decrease according to demand.

---

# 🗄️ 7. Amazon RDS

I studied AWS managed relational database services and their availability options.

### Topics Covered

* Amazon RDS
* Database engines
* MySQL
* PostgreSQL
* MariaDB
* Oracle
* SQL Server
* Automated backups
* Snapshots
* Multi-AZ deployment
* Read Replicas
* Database failover

### 💡 Multi-AZ

```text
              Application
                   │
                   ▼
             RDS Primary
                AZ-A
                   │
            Synchronous
             Replication
                   │
                   ▼
             RDS Standby
                AZ-B
```

**Primary purpose:**

🛡️ High Availability & Disaster Recovery

---

### 💡 Read Replicas

```text
               RDS Primary
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
       Replica-1 Replica-2 Replica-3
```

**Primary purpose:**

⚡ Improve **read scalability/performance**.

One of the important distinctions I learned is:

> **Multi-AZ = High Availability**
> **Read Replicas = Read Scalability**

---

# 🚀 8. Amazon Aurora

I studied Amazon Aurora and how it differs from traditional RDS database deployments.

### Topics Covered

* Aurora architecture
* Aurora MySQL compatibility
* Aurora PostgreSQL compatibility
* Aurora Replicas
* High Availability
* Automatic failover
* Distributed storage
* Aurora scaling concepts

### 💡 Key Learning

Aurora is designed as a cloud-native relational database with distributed storage and strong availability and scalability capabilities.

---

# 🌎 9. Amazon Route 53

I studied AWS's highly available DNS service.

### Topics Covered

* DNS fundamentals
* Domain registration
* Hosted Zones
* DNS records
* A Records
* AAAA Records
* CNAME
* Alias Records
* TTL
* Health Checks

### Routing Policies Covered

✔️ Simple Routing
✔️ Weighted Routing
✔️ Latency-Based Routing
✔️ Failover Routing
✔️ Geolocation Routing
✔️ Geoproximity concepts
✔️ Multi-Value Answer Routing

### Architecture Example

```text
                     User
                       │
                       ▼
                   Route 53
                       │
                 DNS Resolution
                       │
                       ▼
                      ALB
                    /     \
                   ▼       ▼
                 EC2       EC2
```

### 💡 Key Learning

Route 53 is much more than basic DNS.

Routing policies and health checks can be used to design architectures for:

🌎 Global applications
🛡️ Failover
⚡ Low latency
⚖️ Traffic distribution

---

# 🏗️ Connecting Everything Together

The biggest lesson so far has been understanding that AWS services are rarely used independently.

A basic highly available AWS application could look like:

```text
                         INTERNET
                             │
                             ▼
                         Route 53
                             │
                             ▼
                    Application Load
                        Balancer
                             │
                    ┌────────┴────────┐
                    │                 │
                   AZ-A              AZ-B
                    │                 │
                   EC2               EC2
                    │                 │
                    └───────┬─────────┘
                            │
                           EFS
                            │
                            ▼
                       RDS / Aurora
                        Multi-AZ
```

With:

```text
IAM
 │
 └── Controls access and permissions

Auto Scaling
 │
 └── Controls EC2 capacity

ALB
 │
 └── Distributes application traffic

EBS
 │
 └── Provides block storage

EFS
 │
 └── Provides shared file storage

RDS / Aurora
 │
 └── Provides relational database services

Route 53
 │
 └── Provides DNS and routing
```

---

# 🧠 What I Am Focusing on Understanding

Instead of memorizing AWS services, I am trying to answer five questions for every service:

### 1️⃣ What problem does this service solve?

### 2️⃣ When should I use it?

### 3️⃣ When should I NOT use it?

### 4️⃣ How does it integrate with other AWS services?

### 5️⃣ How can I make the architecture secure, highly available and cost-effective?

---

# 🎯 SAA-C03 Exam Domains

My current studies are building knowledge across the four SAA-C03 architecture domains:

| Domain                                 |  Weight |
| -------------------------------------- | ------: |
| 🔐 Design Secure Architectures         | **30%** |
| 🛡️ Design Resilient Architectures     | **26%** |
| ⚡ Design High-Performing Architectures | **24%** |
| 💰 Design Cost-Optimized Architectures | **20%** |

The services studied so far are particularly helping me understand **security, high availability, fault tolerance, scalability and performance**.

---

# 🧪 Next Step — Architecture Labs

Before moving further, my next goal is to combine these individual services into practical AWS architectures.

### Planned Labs

```text
LAB 01
EC2 + IAM Role + EBS

        ↓

LAB 02
ALB + EC2 + Multi-AZ

        ↓

LAB 03
ALB + Auto Scaling + EC2

        ↓

LAB 04
EC2 + EFS Shared Storage

        ↓

LAB 05
Route 53 + ALB + ASG + RDS
```

For each architecture I plan to:

**BUILD → TEST → BREAK → TROUBLESHOOT → FIX → SECURE**

---

# 📖 Next Topic

## 🪣 Amazon S3 — Simple Storage Service

My next major AWS topic will be Amazon S3, including:

* S3 Buckets & Objects
* Storage Classes
* Versioning
* Encryption
* Bucket Policies
* Lifecycle Rules
* Replication
* Static Website Hosting
* S3 Security
* S3 Performance

---

# 🛡️ Long-Term Direction

AWS Solutions Architect Associate is the foundation of a larger learning journey.

```text
AWS Solutions Architect Associate
              │
              ▼
      AWS Architecture Skills
              │
       ┌──────┴──────┐
       ▼             ▼
  Networking     Cloud Security
       │             │
       └──────┬──────┘
              ▼
      Security Specialization
              │
              ▼
    ☁️ Cloud Security
    🌐 Network Security
    🛡️ Cybersecurity
```

My long-term goal is to develop strong expertise in **AWS Cloud Architecture, Cloud Security and Network Security** through a combination of certification study and practical hands-on experience.

---

## 🚀 Learning in Public

This repository represents my ongoing AWS journey.

There is still a lot to learn, but every service studied and every architecture built adds another piece to the bigger picture.

> ### ☁️ Learn it. Build it. Break it. Fix it. Secure it.

**Next milestone: Amazon S3 🪣**

---

⭐ *Repository will be continuously updated as I progress through AWS SAA-C03.*
