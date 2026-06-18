# Maras Solutions — Corporate Website

> **Technology × Management × Field Experience**  
> Real Expertise. Real Solutions. Real Results.

Official website for [Maras Solutions](https://maras.solutions) — a consulting and technology firm bridging business management and modern technology for manufacturing, distribution, and service companies across Saudi Arabia and the GCC.

Built as a single-page HTML/JS site, served via Nginx in Docker, and deployed on a GCP Ubuntu VM.

---

## 📁 Project Structure

```
maras-website/
├── .github/
│   └── workflows/                      # CI/CD: build Docker image & deploy to GCP
├── assets/                             # Images, icons, fonts, and static media
├── screenshots/                        # Site screenshots
├── uploads/                            # Uploaded assets
├── Maras Solutions.dc.html             # Main website (single-page)
├── Maras Solutions (standalone).html   # Standalone version
├── Maras Design System.dc.html         # Design system reference
├── Maras Solutions-print.dc.html       # Print stylesheet version
├── Maras_Solutions_Website_Content.docx # Content source document
├── index.html                          # Root redirect → main HTML file
├── support.js                          # Frontend support script
├── default.conf                        # Nginx server configuration
├── Dockerfile                          # Nginx-based Docker image
├── .dockerignore                       # Files excluded from Docker build
└── .thumbnail                          # Site thumbnail
```

---

## 🚀 Deployment Pipeline

### Overview

```
Push to main
    │
    ▼
GitHub Actions
    │  ├── Build Docker image (Nginx + static files)
    │  └── Push image to container registry
    │
    ▼
GCP Ubuntu VM
    └── docker compose pull && docker compose up -d
```

### GitHub Actions

The workflow (`.github/workflows/`) triggers on every push to `main` and:

1. Builds the Docker image from the `Dockerfile`
2. Pushes it to the container registry
3. SSHs into the GCP VM and redeploys via Docker Compose

### Required GitHub Secrets

Set these under **GitHub → Settings → Secrets and variables → Actions**:

| Secret | Description |
|--------|-------------|
| `GCP_SSH_KEY` | Private SSH key for the GCP VM |
| `GCP_HOST` | Public IP or hostname of the GCP VM |
| `GCP_USER` | SSH username (e.g. `ubuntu`) |
| `REGISTRY_USERNAME` | Container registry username |
| `REGISTRY_PASSWORD` | Container registry password / token |

> Adjust names to match what's defined in your workflow YAML.

---

## 🐳 Docker & Local Development

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Run Locally

```bash
# Clone the repo
git clone https://github.com/skienlabs/maras-website.git
cd maras-website

# Build and run
docker build -t maras-website .
docker run -p 8080:80 maras-website
```

Then open [http://localhost:8080](http://localhost:8080) in your browser.

### With Docker Compose (mirrors production)

```bash
docker compose up --build
```

---

## 🌐 Site Sections

| Section | Description |
|---------|-------------|
| **Hero** | Tagline, CTA buttons (Free Consultation / Explore Services) |
| **What Sets Us Apart** | 3 integrated disciplines, F&B focus, zero IoT subscription fees |
| **Why Maras** | Field experience differentiators vs. typical consulting firms |
| **Our Services** | Business consulting, financial consulting, IT solutions |
| **About Us** | Company story, vision, mission, and core values |
| **Industries** | Manufacturing, F&B, Retail & Distribution, Salons, SMEs |
| **Contact** | Contact form + email/location info |

---

## 🛠️ Services

### Business & Operations Consulting
- Factory management, time & cost reduction
- Quality elevation & technology system implementation
- Distribution efficiency & sales development
- HR, procurement & logistics support

### Financial Consulting & Accounting
- Financial auditing & internal controls
- Outsourced bookkeeping (subscription-based)
- Freelance accounting teams on demand
- Feasibility & quality studies

### Information Technology
- Custom software & e-commerce platforms
- Fleet management system
- Production & quality / OEE application
- Salon POS & IoT solutions *(zero recurring subscription fees)*

---

## 🏭 Industries Served

Manufacturing · Food & Beverage · Retail & Distribution · Salons & Beauty · SMEs

---

## 📞 Contact

| | |
|---|---|
| 📧 Email | hello@maras.solutions |
| 📍 Location | Saudi Arabia — serving the GCC, Egypt & Africa |
| 🔗 LinkedIn | [Maras Solutions](https://linkedin.com) |

---

## 🇸🇦 Vision Alignment

Maras Solutions operates in full alignment with the goals of **Saudi Vision 2030**, empowering SMEs and mid-market companies to digitize operations and adopt enterprise-grade management practices.

---

## 📄 License

Private repository — © 2026 Maras Solutions. All rights reserved.
