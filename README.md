# 🚀 AWS ECS DevOps Project (Node.js App Deployment)

## 📌 Project Overview

This project demonstrates a complete **DevOps deployment pipeline on AWS** by containerizing and deploying a Node.js application using ECS Fargate.

---

## 🧱 Architecture

```
GitHub → Docker → ECR → ECS (Fargate) → Public Access → CloudWatch Logs
```

---

## ⚙️ Tech Stack

* Node.js
* Docker
* AWS EC2 (for setup)
* AWS ECR (Elastic Container Registry)
* AWS ECS (Fargate)
* AWS IAM
* AWS CloudWatch

---

## 🚀 Steps Performed

### 1️⃣ Clone Repository

```bash
git clone <your-repo-url>
cd <project-folder>
```

---

### 2️⃣ Create Docker Image

```bash
docker build -t node-app .
```

---

### 3️⃣ Tag & Push to ECR

```bash
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com

docker tag node-app:latest <ECR_URI>
docker push <ECR_URI>
```

---

### 4️⃣ Create ECS Cluster

* Launch type: **Fargate**
* Cluster created successfully

---

### 5️⃣ Task Definition

* Container image from ECR
* Port mapping: **8000**
* CPU/Memory configured

---

### 6️⃣ Run Task / Service

* Deployed container on ECS
* Application started successfully

---

### 7️⃣ Security Group Fix 🔐

Initially app was not accessible.

✅ Solution:

* Opened inbound rule:

```
Port: 8000
Source: 0.0.0.0/0
```

---

### 8️⃣ Monitoring 📊

* Logs verified in CloudWatch
* Output:

```
Todolist running on http://0.0.0.0:8000
```

---

## 🌐 Application Access

```
http://<public-ip>:8000
```

---

## 🧠 Key Learnings

* Containerization using Docker
* AWS ECS deployment (Fargate)
* Working with ECR
* IAM role & permissions setup
* Debugging networking issues (ports & security groups)
* Monitoring using CloudWatch

---

## ⚡ Future Improvements

* Add Application Load Balancer
* Setup CI/CD using GitHub Actions
* Add custom domain & HTTPS
* Implement auto-scaling

---

## 📷 Screenshots (Optional)

*Add screenshots of ECS, ECR, CloudWatch logs here*

---

## 🙌 Conclusion

This project helped in understanding real-world DevOps workflows and AWS deployment strategies.

---

## ⭐ Give a Star

If you found this project helpful, please give it a ⭐ on GitHub!
