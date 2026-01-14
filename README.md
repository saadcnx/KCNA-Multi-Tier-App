# Kubernetes Multi-Tier Application

This project demonstrates the deployment of a complete **multi-tier application** on Kubernetes using best practices.  
The architecture consists of **Frontend**, **Backend**, and **Database** tiers, each deployed and managed independently.

---

## Architecture Overview

Frontend (Nginx) → Backend (Python Flask API) → Database (MySQL)

Each tier communicates internally using Kubernetes Services, ensuring secure and reliable service discovery.

---

## Technologies Used

- Kubernetes
- Docker
- Nginx
- Python (Flask)
- MySQL
- ConfigMaps & Secrets
- Kubernetes Services (ClusterIP, NodePort)

---

## Components

### 1. Database Tier
- MySQL database deployed as a Kubernetes Deployment
- Internal access via ClusterIP Service
- Configuration handled using ConfigMaps
- Credentials managed using Kubernetes Secrets

### 2. Backend Tier
- Python Flask REST API
- Connects securely to MySQL database
- Exposes health and data endpoints
- Scaled using multiple replicas
- Uses readiness and liveness probes

### 3. Frontend Tier
- Nginx serving static HTML
- Reverse proxy to backend API
- Exposed externally using NodePort Service

---

## Key Kubernetes Concepts Implemented

- Multi-tier architecture
- Pod-to-Pod communication
- Service discovery using Kubernetes DNS
- Externalized configuration with ConfigMaps
- Secure secret management
- Horizontal scaling of services
- Health checks and probes

---

## Deployment Steps

```bash
# Create namespace
kubectl apply -f namespace.yaml

# Deploy database tier
kubectl apply -f database/

# Deploy backend tier
kubectl apply -f backend/

# Deploy frontend tier
kubectl apply -f frontend/

Accessing the Application
Copy code
kubectl get service frontend-service

Open the browser using:
php-template
Copy code
http://<NODE_IP>:<NODE_PORT>

# Verification
Frontend loads successfully
Backend health endpoint responds
Backend connects to MySQL database
Services resolve using internal DNS
Scaling frontend and backend works as expected

# Learning Outcomes
Designed and deployed a real-world Kubernetes multi-tier application
Implemented secure inter-service communication
Applied Kubernetes configuration and secret management best practices
Gained hands-on experience with scaling and troubleshooting

# Future Improvements:
Persistent Volumes for database storage
Ingress Controller for external access
CI/CD pipeline integration
Monitoring with Prometheus & Grafana

Practical completed at Al Nafi International College.
