# 🌍 Wanderlust - Full-Stack Travel Blog & CI/CD DevOps Platform

**Wanderlust** is a production-grade, full-stack travel blog application featuring an automated, security-aware CI/CD pipeline deployed on AWS. The platform enables users to explore featured and latest posts, filter stories by categories (Travel, Nature, City, Adventure, Beaches, Landmarks), and create new travel entries.

---

## 🚀 Live Deployment & Access

* **Live Application (React Frontend):** [http://13.61.153.80:5173/](https://www.google.com/search?q=http://13.61.153.80:5173/)
* **GitHub Repository:** [saneecalokhande-cpu/Wanderlust-Mega-Project](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/saneecalokhande-cpu/Wanderlust-Mega-Project.git)
* **Hosting Region:** AWS Europe (Stockholm), `eu-north-1`

---

## 🛠️ Tech Stack & DevOps Toolchain

| Category | Technology / Tool | Purpose in Project |
| --- | --- | --- |
| **Frontend** | React, Vite | Responsive user interface and dynamic views |
| **Backend** | Node.js, Express.js | RESTful API server handling blog posts and categories |
| **Database** | MongoDB | NoSQL database for persistent storage of posts and user data |
| **Caching** | Redis (`redis:7.8.5-alpine`) | High-performance caching layer |
| **Cloud Infrastructure** | Amazon EC2 (`m7i-flex.large`, Ubuntu) | Compute instance hosting the application and automation servers |
| **CI/CD Orchestration** | Jenkins (Declarative Pipeline) | Automates build, test, scan, and deployment stages |
| **Code Quality (SAST)** | SonarQube (`sonarqube:lts-community`) | Static code analysis, bug tracking, and Quality Gate evaluation |
| **Security Scanning** | Trivy & OWASP Dependency-Check | File system, dependency CVE, and container image security scanning |
| **Containerization** | Docker & Docker Compose | Multi-container packaging and orchestration (`-backend`, `-frontend`, `mongo`, `redis`, `sonarqube`) |

---

## 📂 Project Architecture & Directory Structure

```text
Wanderlust-Mega-Project/
├── backend/            # Node.js & Express REST API
├── frontend/           # React single-page application
├── kubernetes/         # K8s deployment manifests (Future scope)
├── terraform/          # Infrastructure as Code scripts (Future scope)
├── Jenkinsfile         # Declarative CI/CD pipeline definition
├── docker-compose.yml  # Multi-container service orchestration
├── package.json        # Project dependencies and scripts
└── package-lock.json   # Locked dependency versions

```

---

## ⚡ CI/CD Pipeline Workflow

The automated Jenkins declarative pipeline executes the following stages on every build:

1. **Clone Code:** Pulls the latest source code from the main branch of the GitHub repository.
2. **SonarQube Analysis:** Performs static code analysis checking for bugs, vulnerabilities, and code smells across ~1.5k lines of JavaScript.
3. **Quality Gate Evaluation:** Waits for SonarQube Quality Gate status (`waitForQualityGate`) to validate code health.
4. **Trivy File System Scan:** Scans the repository file system using Aqua Security's Trivy to catch vulnerabilities early.
5. **Docker Compose Deployment:** Builds backend and frontend container images and deploys the full stack (`mongo`, `redis`, backend, frontend) via `docker-compose up -d`.

---

## 🔌 Port Mapping & Networking

Security Groups on AWS EC2 control inbound traffic across the following ports:

* **Port 22:** SSH Access
* **Port 8080:** Jenkins Automation Server
* **Port 9000:** SonarQube Dashboard
* **Port 5173:** Wanderlust React Frontend Application

---

## 🚀 Local Development & Setup

Follow these instructions to run the application locally or set up the infrastructure environment.

### **Prerequisites**

* [Node.js](https://nodejs.org/) (v18+)
* [Docker](https://www.docker.com/) & [Docker Compose](https://docs.docker.com/compose/)
* [MongoDB](https://www.mongodb.com/) and [Redis](https://redis.io/)

### **1. Clone the Repository**

```bash
git clone https://github.com/saneecalokhande-cpu/Wanderlust-Mega-Project.git
cd Wanderlust-Mega-Project

```

### **2. Run with Docker Compose**

To spin up the entire application stack locally:

```bash
docker-compose up -d

```

### **3. Manual Execution**

* **Backend:**
```bash
cd backend
npm install
npm start

```


* **Frontend:**
```bash
cd frontend
npm install
npm run dev

```



---

## 👤 Author

* **Saneeca Lokhande** - *[saneecalokhande-cpu](https://www.google.com/search?q=https://github.com/saneecalokhande-cpu)*

---

## 📜 License

Distributed under the MIT License. See [LICENSE](https://www.google.com/search?q=LICENSE) for details.
