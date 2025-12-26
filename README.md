Foodyme Frontend – Kubernetes Application Deployment
📌 Project Overview

Foodyme is a frontend web application that I containerized using Docker and deployed on Kubernetes.
This project demonstrates real-world Kubernetes application development practices, starting from containerization to orchestration, scaling, configuration management, and debugging.

The application is deployed and tested using Minikube (local Kubernetes cluster), following production-style Kubernetes workflows.

🏗️ Architecture Overview
User
  ↓
Kubernetes Service
  ↓
Pods (Nginx + Frontend App)
  ↓
Docker Image (Docker Hub)

🛠️ Tools & Technologies Used

Frontend: React (static build)

Containerization: Docker (multi-stage Dockerfile)

Web Server: Nginx

Orchestration: Kubernetes

Local Kubernetes Cluster: Minikube

CI/CD: GitHub Actions

Container Registry: Docker Hub

📦 Kubernetes Components Used

Deployment – manages pod replicas and self-healing

Service (NodePort) – exposes the application inside the cluster

ConfigMap – stores non-sensitive configuration

Secret – stores sensitive configuration

Liveness Probe – restarts unhealthy containers

Readiness Probe – controls traffic routing

Resource Requests & Limits – CPU and memory management

Horizontal Pod Autoscaler (HPA) – automatic scaling based on CPU usage

🚀 Application Workflow

Frontend source code is built into a Docker image

Static build files are served using Nginx

Kubernetes Deployment manages pod lifecycle

Service provides stable networking and load balancing

ConfigMaps and Secrets externalize configuration

Health probes ensure self-healing

HPA automatically scales pods based on load

▶️ How to Run the Application Locally (Minikube)
1️⃣ Start Minikube
minikube start

2️⃣ Apply Kubernetes Manifests (Correct Order)
kubectl apply -f configmap.yaml
kubectl create secret generic foodyme-secret \
--from-literal=DB_PASSWORD=foodyme123
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f hpa.yaml

3️⃣ Verify Pods
kubectl get pods

4️⃣ Access the Application
minikube service foodyme-service

📈 Auto-Scaling with HPA

Minimum replicas: 2

Maximum replicas: 5

Scaling metric: CPU utilization (50%)

Kubernetes automatically scales pods up during high load and scales them down when traffic decreases.

🧠 Key Learnings from This Project

Dockerizing frontend applications using multi-stage builds

Kubernetes Deployments and Services

Pod lifecycle and self-healing behavior

Configuration management using ConfigMaps and Secrets

Health checks using liveness and readiness probes

Resource management using CPU and memory limits

Horizontal Pod Autoscaling

Debugging Kubernetes issues such as:

CreateContainerConfigError

Missing Secrets and ConfigMaps

Cluster restarts and recovery

CI/CD automation using GitHub Actions

🔁 CI/CD Pipeline Overview

This project includes a GitHub Actions CI/CD pipeline that:

Triggers on every GitHub push

Builds a Docker image automatically

Pushes the image to Docker Hub

This ensures consistent and automated container builds.

👨‍💻 Author

Adi Sesha