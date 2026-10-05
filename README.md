# 🛡️ AI-Based Fake Identity & Document Screening System

<div align="center">

[![Smart India Hackathon 2026](https://img.shields.io/badge/SIH-2026-blue?style=flat-square&logo=github)](https://www.sih.gov.in/)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-green?style=flat-square&logo=python)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009485?style=flat-square&logo=fastapi)](https://fastapi.tiangolo.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

**AI-powered document verification, tampering detection, and biometric identity verification system**

[Quick Start](#-quick-start) • [Features](#-key-features) • [Workflow](#-end-to-end-workflow) • [Installation](#-installation--setup) • [API Docs](#-api-overview) • [Live Demo](#-live-demo)

</div>

---

## 📋 Table of Contents

1. [Project Overview](#-project-overview)
2. [Problem Statement](#-problem-statement)
3. [Our Solution](#-our-solution)
4. [Key Features](#-key-features)
5. [Quick Start](#-quick-start)
6. [End-to-End Workflow](#-end-to-end-workflow)
7. [Verification Pipeline](#-verification-pipeline)
8. [Technology Stack](#-technology-stack)
9. [System Architecture](#-system-architecture)
10. [Project Structure](#-project-structure)
11. [Installation & Setup](#-installation--setup)
12. [Environment Variables](#-environment-variables)
13. [How to Run Locally](#-how-to-run-locally)
14. [API Overview](#-api-overview)
15. [Supported Documents](#-supported-documents)
16. [Application Areas](#-application-areas)
17. [Security & Privacy Considerations](#-security--privacy-considerations)
18. [Limitations](#-limitations)
19. [Current Implementation Status](#-current-implementation-status)
20. [Future Scope](#-future-scope)
21. [Team & Contributors](#-team--contributors)

---

## 🎯 Project Overview

This project presents an **AI-powered identity and document screening system** designed to detect potentially **fake or tampered identity documents** and verify whether the person presenting the document corresponds to the portrait on the document through **biometric facial matching**.

The system is being developed for **Smart India Hackathon 2026** and combines advanced computer vision, OCR, and forensic analysis to provide a comprehensive document and identity verification solution.

### Core Capabilities:
- **Document Verification**: Automated detection of document type, extraction of fields, and tampering detection
- **Biometric Verification**: Live facial capture and comparison with document portrait
- **Risk Scoring**: Explainable 0-100 risk score for each document
- **Forensic Analysis**: Digital forensics to detect image manipulation
- **Multi-Document Support**: PAN Card, Aadhaar, Voter ID, Passport

---

## 🔍 Problem Statement

In the digital age, identity fraud and document tampering pose significant challenges to:
- **KYC (Know Your Customer)** processes in banking and finance
- **Government services** and citizen verification
- **Insurance and recruitment** onboarding
- **Digital service platforms** requiring identity verification

Current solutions either:
- Rely on manual verification (slow, expensive, error-prone)
- Lack comprehensive tampering detection
- Cannot correlate document portrait with live biometrics
- Provide limited transparency in decision-making

---

## 💡 Our Solution

We present an **end-to-end AI-driven verification system** that:

1. **Automatically identifies document types** and extracts structured information
2. **Detects tampering and forgery** through digital forensic analysis
3. **Performs statutory/regulatory validation** of document fields
4. **Generates explainable risk scores** for human review
5. **Verifies biometric correspondence** between document and live capture
6. **Combines both signals** into a final verification decision

The system is **transparent, explainable, and designed for real-world deployment** in government, banking, and enterprise environments.

---

## ⭐ Key Features

| Feature | Description |
|---------|-------------|
| 🔐 **Multi-Document Support** | PAN Card, Aadhaar, Voter ID, Passport |
| 📸 **OCR Extraction** | Baidu Unlimited-OCR for high-accuracy field extraction |
| 🤖 **Document Classification** | Automatic document type detection and categorization |
| 🔍 **Tampering Detection** | Digital forensics to identify image manipulation |
| 📊 **Risk Scoring** | Explainable 0-100 risk score with detailed reasoning |
| 👤 **Face Detection** | YuNet-based robust face detection from documents |
| 🎭 **Facial Biometrics** | SFace embeddings and cosine similarity matching |
| 📹 **Live Capture** | Webcam integration for real-time selfie/live capture |
| ✅ **Statutory Validation** | Regulatory compliance checks for document fields |
| 🎯 **Final Decision Engine** | Combined document + biometric verification decision |
| 🌐 **Web Interface** | Intuitive HTML5/CSS3/JavaScript frontend |
| ⚡ **REST API** | FastAPI-based backend for integration |

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- NVIDIA GPU (optional, for faster processing)
- Webcam/Camera for biometric verification
- Modern web browser with JavaScript enabled

### Installation (5 minutes)

```bash
# Clone the repository
git clone https://github.com/soluofficial/ai-fake-identity-document-screening.git
cd ai-fake-identity-document-screening

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Run the application
python main.py
```

**Access the application:**
- Frontend: `http://localhost:8000`
- API Docs: `http://localhost:8000/docs`

---

## 🔄 End-to-End Workflow

### Phase 1: Document Verification

```
User Uploads Document
         ↓
Unlimited-OCR (Extract Text & Fields)
         ↓
Document Discriminator (Identify Type)
         ↓
Statutory Validation (Verify Field Compliance)
         ↓
Digital Forensics (Detect Tampering)
         ↓
Risk Scoring Engine (Generate 0-100 Score)
         ↓
Document Decision (PASS / REVIEW / FAIL)
```

### Phase 2: Identity Verification

```
Portrait Extracted from Document
         ↓
Live Webcam/Selfie Capture
         ↓
YuNet Face Detection (Both images)
         ↓
SFace Facial Embeddings (Generate vectors)
         ↓
Cosine Similarity (Calculate match score)
         ↓
Classification (MATCH / REVIEW / MISMATCH)
```

### Phase 3: Final Decision

```
Document Verification Result
         +
Biometric Verification Result
         ↓
Final Decision Engine
         ↓
APPROVED / NEEDS_REVIEW / REJECTED
```

---

## ⚙️ Verification Pipeline

| Stage | Component | Purpose | Input | Output |
|-------|-----------|---------|-------|--------|
| 1 | **OCR Extraction** | Extract text and metadata from document image | Document image | Structured fields, regions, metadata |
| 2 | **Document Discriminator** | Identify document type | Extracted fields | Document type classification |
| 3 | **Statutory Validation** | Verify field compliance with regulations | Extracted fields | Validation status, compliance flags |
| 4 | **Digital Forensics** | Detect image manipulation/tampering | Document image | Forensic risk indicators |
| 5 | **Risk Scoring** | Generate explainable risk score | All forensic + validation data | 0-100 risk score, explanation |
| 6 | **Document Decision** | Produce document verification verdict | Risk score, validation result | PASS / REVIEW / FAIL |
| 7 | **Face Detection** | Locate and extract faces | Document + live capture images | Face bounding boxes, coordinates |
| 8 | **Facial Embeddings** | Generate vector representations | Face images | High-dimensional embedding vectors |
| 9 | **Similarity Matching** | Calculate facial correspondence | Document embedding, live embedding | Cosine similarity score (0-1) |
| 10 | **Biometric Decision** | Classify face match status | Similarity score | MATCH / REVIEW / MISMATCH |
| 11 | **Final Decision** | Combine both results | Document + Biometric decisions | APPROVED / NEEDS_REVIEW / REJECTED |

---

## 🏛️ Technology Stack

### Frontend
| Technology | Purpose | Version |
|------------|---------|---------|
| **HTML5** | Document structure and semantics | Latest |
| **CSS3** | Responsive styling and UI design | Latest |
| **JavaScript** | Client-side interactivity | ES6+ |
| **Web Camera API** | Live capture from webcam | Native API |

### Backend
| Technology | Purpose | Version |
|------------|---------|---------|
| **Python** | Backend programming language | 3.8+ |
| **FastAPI** | Web framework for REST API | 0.100+ |
| **Pydantic** | Data validation and serialization | 2.0+ |
| **Uvicorn** | ASGI server | Latest |

### AI & Computer Vision
| Technology | Purpose | Notes |
|------------|---------|-------|
| **Baidu Unlimited-OCR** | Text extraction from documents | Cloud-based API |
| **YuNet** | Face detection from images | OpenCV-based |
| **SFace** | Facial embedding generation | Pre-trained model |
| **OpenCV** | Image processing and manipulation detection | 4.8+ |
| **NumPy** | Numerical computation | Latest |
| **Scikit-learn** | Cosine similarity and ML utilities | Latest |

### Infrastructure & Development
| Component | Specification | Notes |
|-----------|---------------|-------|
| **OS** | Windows, WSL2, Ubuntu | Tested on all platforms |
| **GPU** | NVIDIA CUDA | Optional, for faster processing |
| **GPU Model** | NVIDIA RTX 4050 Laptop | Tested configuration |
| **GPU Memory** | 6GB VRAM | Minimum recommended |
| **IDE** | VS Code | Recommended |
| **Version Control** | Git & GitHub | For collaboration |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER INTERFACE                           │
│                  (HTML5/CSS3/JavaScript)                        │
│            - Document Upload                                    │
│            - Live Webcam Capture                                │
│            - Result Display                                     │
└──────────────────────┬──────────────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────────┐
│                      REST API (FastAPI)                         │
│         - /upload-document (POST)                               │
│         - /verify-document (POST)                               │
│         - /capture-selfie (POST)                                │
│         - /verify-identity (POST)                               │
│         - /get-result (GET)                                     │
└──────────────────────┬──────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
    ┌────────────┐ ┌─────────────┐ ┌──────────────────┐
    │  OCR       │ │   Face      │ │  Risk Scoring    │
    │  Module    │ │ Biometrics  │ │  & Decision      │
    │            │ │  Module     │ │  Engine          │
    │ Unlimited  │ │             │ │                  │
    │ Unlimited- │ │ - YuNet     │ │ - Forensics      │
    │ OCR        │ │ - SFace     │ │ - Validation     │
    │            │ │ - Cosine    │ │ - Scoring        │
    └────────────┘ │   Similarity│ └──────────────────┘
                   │             │
                   └─────────────┘
                       │
                       ▼
    ┌────────────────────────────────┐
    │   Database / Result Storage    │
    │   (File/Database to define)    │
    └────────────────────────────────┘
```

---

## 📂 Project Structure

Refer to the project configuration/source code for the current implementation of the directory structure. Key files and directories are:

```
ai-fake-identity-document-screening/
├── README.md                    # Project documentation
├── .env.example                 # Environment variables template
├── .gitignore                   # Git ignore rules
├── requirements.txt             # Python dependencies
├── main.py                      # Application entry point
├── LICENSE                      # MIT License
│
├── backend/                     # Backend application code
│   ├── app.py                  # FastAPI application
│   ├── models/                 # Data models (Pydantic)
│   ├── routes/                 # API endpoints
│   ├── services/               # Business logic
│   │   ├── ocr_service.py
│   │   ├── document_classifier.py
│   │   ├── face_biometrics.py
│   │   ├── forensics.py
│   │   └── decision_engine.py
│   └── utils/                  # Utility functions
│
├── frontend/                    # Frontend application
│   ├── index.html              # Main page
│   ├── css/                    # Stylesheets
│   └── js/                     # JavaScript files
│
├── models/                      # Pre-trained AI models
│   ├── yunet.onnx              # Face detection model
│   └── sface.onnx              # Facial embedding model
│
├── docs/                        # Documentation
│   ├── ARCHITECTURE.md          # Detailed architecture
│   ├── API.md                   # API reference
│   └── SETUP.md                 # Detailed setup guide
│
└── tests/                       # Unit and integration tests
    ├── test_ocr.py
    ├── test_biometrics.py
    └── test_forensics.py
```

**Note:** Refer to the project configuration/source code for the current implementation of the actual directory structure and files.

---

## 🛠️ Installation & Setup

### System Requirements

- **Python:** 3.8 or higher
- **RAM:** 8GB minimum, 16GB+ recommended
- **GPU:** NVIDIA GPU with CUDA support (optional, for faster processing)
- **Storage:** 2GB minimum (models + dependencies)
- **OS:** Windows, macOS, or Linux (Ubuntu 20.04+)

### Step 1: Clone the Repository

```bash
git clone https://github.com/soluofficial/ai-fake-identity-document-screening.git
cd ai-fake-identity-document-screening
```

### Step 2: Create Virtual Environment

```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Step 4: Download Models

Refer to the project configuration/source code for the current implementation of model download and setup procedures.

### Step 5: Configure Environment

```bash
cp .env.example .env
```

Edit `.env` with your configuration:

```bash
nano .env  # or use your favorite editor
```

---

## 🔑 Environment Variables

Refer to the project configuration/source code for the complete list of required environment variables.

**Common environment variables (if applicable):**

```env
# Application
APP_NAME=AI-Based Fake Identity & Document Screening
APP_VERSION=1.0.0
DEBUG=False
ENVIRONMENT=development

# Server
HOST=0.0.0.0
PORT=8000
WORKERS=4

# API Keys and Credentials
BAIDU_OCR_API_KEY=your_baidu_api_key
BAIDU_OCR_SECRET_KEY=your_baidu_secret_key

# Model Configuration
MODEL_PATH=models/
FACE_DETECTION_THRESHOLD=0.5
SIMILARITY_THRESHOLD=0.65

# Database
DATABASE_URL=sqlite:///./documents.db

# Logging
LOG_LEVEL=INFO
LOG_FILE=app.log

# CORS
CORS_ORIGINS=http://localhost:3000,http://localhost:8000
```

**⚠️ Security Note:** Never commit `.env` file with real secrets. Always use `.env.example` as template.

---

## ▶️ How to Run Locally

### Development Mode

```bash
# Activate virtual environment (if not already activated)
source venv/bin/activate  # macOS/Linux
# or
venv\Scripts\activate     # Windows

# Run the application
python main.py

# Or using Uvicorn directly
uvicorn backend.app:app --reload --host 0.0.0.0 --port 8000
```

### Production Mode

```bash
uvicorn backend.app:app --host 0.0.0.0 --port 8000 --workers 4
```

### Access the Application

- **Frontend:** `http://localhost:8000`
- **API Documentation:** `http://localhost:8000/docs` (Swagger UI)
- **ReDoc:** `http://localhost:8000/redoc` (Alternative API docs)

---

## 📡 API Overview

### Core Endpoints

Refer to the project configuration/source code for the current implementation of API endpoints and complete documentation.

**Expected endpoint structure:**

| Endpoint | Method | Purpose | Status |
|----------|--------|---------|--------|
| `/api/v1/health` | GET | Health check | To be confirmed |
| `/api/v1/upload-document` | POST | Upload and process document | To be confirmed |
| `/api/v1/verify-document` | POST | Verify document authenticity | To be confirmed |
| `/api/v1/capture-selfie` | POST | Upload selfie image | To be confirmed |
| `/api/v1/verify-identity` | POST | Verify facial biometrics | To be confirmed |
| `/api/v1/results/{request_id}` | GET | Retrieve verification results | To be confirmed |

### Example Request/Response

Refer to the project configuration/source code for example API calls and response schemas.

---

## 📋 Example Workflow

### Workflow: Complete Identity Verification

```
1. User opens web interface
2. User selects document type and uploads image
   → API receives document
   → Baidu OCR extracts text fields
   → Document Discriminator confirms type
   → Statutory Validation checks compliance
   → Digital Forensics analyzes for tampering
   → Risk Score generated (e.g., 25/100)
   → Document Decision: PASS

3. System prompts for live selfie
   → User captures selfie via webcam
   → API receives image

4. Facial Biometrics Processing
   → YuNet detects faces in both images
   → SFace generates embeddings
   → Cosine similarity calculated (e.g., 0.87)
   → Classification: MATCH

5. Final Decision
   → Document PASS + Biometric MATCH
   → Final Result: APPROVED
   → User receives success notification
```

---

## 🔒 Security & Privacy Considerations

### Data Protection

- **No permanent storage** of sensitive personal data (unless explicitly required for audit)
- **Encrypted transmission** of images and biometric data
- **HTTPS only** in production environments
- **Input validation** on all API endpoints
- **Rate limiting** to prevent abuse

### Privacy

- **User consent** required before processing biometric data
- **Clear privacy policy** explaining data usage
- **GDPR/India data protection compliance** (refer to legal guidelines)
- **Minimal data retention** policy (delete data after verification)
- **Audit logging** of all verification attempts

### Biometric Safety

- **Facial similarity score** indicates correspondence between document portrait and live capture
- **This is NOT a probability** of real-world identity or authorization
- **Human review recommended** for sensitive transactions
- **Anti-spoofing measures** should be implemented (liveness detection)
- **Facial matching threshold** should be configurable based on risk tolerance

### Government Integration

⚠️ **Important:** This system does **NOT automatically access government identity databases**.

- Government API integration (if required) must be:
  - Explicitly configured by administrators
  - Subject to all applicable laws and regulations
  - Used only with proper authorization
  - Logged and audited
  - Integrated only if the repository contains actual implementation

---

## ⚠️ Limitations

### Current Limitations

1. **Facial Similarity ≠ Identity Proof**
   - The facial similarity score only indicates whether the live capture matches the document portrait
   - It does NOT constitute legal identity verification
   - It must NOT be used as sole proof of identity without human review

2. **No Government Database Integration**
   - The system does NOT query government identity databases (Aadhaar, passport databases, etc.)
   - Such integration requires explicit authorization, legal compliance, and API credentials
   - Integration exists only if actual code is present in the repository

3. **Document Tampering Detection Limitations**
   - Forensic analysis can detect common image manipulations (ELA, copy-move, etc.)
   - Sophisticated forgeries may not be detected
   - Professional digital tampering may bypass some checks

4. **Face Detection Limitations**
   - Poor lighting or image quality may reduce accuracy
   - Extreme angles or partial faces may not be detected
   - Masks, glasses, or heavy makeup may affect biometric matching

5. **OCR Limitations**
   - Handwritten information may not be accurately extracted
   - Damaged or low-quality documents may cause errors
   - Non-standard document formats may not be recognized

6. **Geographic & Regulatory Scope**
   - Currently supports specific Indian identity documents
   - International documents not yet supported
   - Legal requirements vary by jurisdiction

### Deployment Limitations

- System requires GPU for optimal performance
- Baidu OCR API requires internet connectivity
- Real-time processing may have latency depending on infrastructure
- Scalability considerations for high-volume deployments

---

## 📊 Current Implementation Status

### ✅ Implemented Features

- [x] Project repository setup
- [x] Basic FastAPI application structure
- [x] Frontend HTML5/CSS3/JavaScript interface

### 🟡 Partially Implemented

Refer to the project configuration/source code for current implementation status of:
- Document upload and processing pipeline
- Baidu Unlimited-OCR integration
- Document discriminator module
- Face detection (YuNet) integration
- Facial embedding (SFace) generation
- Cosine similarity calculation
- Risk scoring engine
- Decision logic
- Biometric verification workflow

### 📅 Planned Features

- [ ] Statutory validation rules engine
- [ ] Digital forensics modules (ELA, copy-move detection, EXIF analysis)
- [ ] Advanced anti-spoofing and liveness detection
- [ ] Batch document processing
- [ ] Audit logging and compliance reporting
- [ ] Role-based access control (RBAC)
- [ ] Multi-language OCR support
- [ ] Cloud deployment templates (AWS, Azure, GCP)
- [ ] Government API integration (with proper authorization)
- [ ] Mobile application (iOS/Android)
- [ ] Enhanced UI/UX
- [ ] Performance optimization and caching
- [ ] Comprehensive test coverage

---

## 🚀 Future Scope

### Phase 2 Enhancements

1. **Additional Document Types**
   - International passports
   - Driver's licenses
   - Government-issued ID cards
   - Banking/financial documents
   - Educational credentials

2. **Enhanced Anti-Spoofing**
   - Liveness detection algorithms
   - Texture analysis
   - Frequency domain analysis
   - Multi-frame video analysis

3. **Improved Forensic Detection**
   - Machine learning-based forgery detection
   - Generative AI detection (deepfake detection)
   - Advanced metadata analysis
   - Blockchain-based document verification

4. **Scalable Cloud Deployment**
   - Containerization (Docker)
   - Kubernetes orchestration
   - Microservices architecture
   - Load balancing and auto-scaling
   - Multi-region deployment

5. **Enterprise Features**
   - Role-based access control (RBAC)
   - Audit logging and compliance reports
   - Webhook notifications
   - Bulk processing APIs
   - Analytics dashboard
   - Custom thresholds and workflows

6. **Government/Enterprise Integrations**
   - Authorized government API integration (Aadhaar, Passport, etc.)
   - Banking KYC system integration
   - Insurance onboarding systems
   - Recruitment platform integration
   - Educational credential verification

7. **Mobile Applications**
   - iOS native application
   - Android native application
   - React Native cross-platform app
   - Progressive Web App (PWA)

8. **Advanced Analytics**
   - Real-time verification dashboard
   - Fraud detection patterns
   - Performance metrics
   - Cost analysis
   - ROI tracking

---

## 📱 Application Areas

This system can be deployed in:

| Sector | Use Case | Benefit |
|--------|----------|---------|
| **Banking & Finance** | KYC (Know Your Customer) verification | Reduce fraud, improve onboarding speed |
| **Government** | Citizen ID verification, benefit distribution | Prevent identity fraud, ensure fairness |
| **Insurance** | Policy holder verification, claims processing | Reduce fraudulent claims |
| **Education** | Student identity verification, credential validation | Prevent credential fraud |
| **Recruitment** | Candidate identity verification | Background check acceleration |
| **Digital Onboarding** | Account creation, service registration | Frictionless but secure onboarding |
| **Healthcare** | Patient identity verification | Prevent medical identity theft |
| **Telecom** | SIM card activation, KYC compliance | Regulatory compliance |
| **Border Control** | Travel document verification | Immigration security |
| **Law Enforcement** | Identity verification in criminal cases | Investigative support |

---

## 📸 Screenshots / Demo

Screenshots from the application will be added to this section upon availability.

**Placeholder for demo images:**
- Document upload interface
- Live verification process
- Results dashboard
- API documentation

---

## 🎬 Live Demo

**[Access the Live Demo](https://ai-basedfakeidentityscreeningsystem.vercel.app/)**

**Note:** The live demo provides access to the frontend interface. Backend processing capabilities may vary depending on deployment configuration. For full feature testing, please install and run locally.

---

## 👥 Team & Contributors

This project is being developed as a submission to **Smart India Hackathon 2026**.

### How to Contribute

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Reporting Issues

Found a bug or have a suggestion? Please [open an issue](https://github.com/soluofficial/ai-fake-identity-document-screening/issues).

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 📧 Contact

For questions, suggestions, or inquiries:
- **GitHub:** [@soluofficial](https://github.com/soluofficial)
- **Repository:** [ai-fake-identity-document-screening](https://github.com/soluofficial/ai-fake-identity-document-screening)

---

## 🙏 Acknowledgments

- **Smart India Hackathon 2026** for the opportunity and platform
- **Baidu Cloud** for Unlimited-OCR technology
- **OpenCV Community** for computer vision tools
- **FastAPI Team** for the excellent web framework
- All contributors and supporters

---

**Made with ❤️ for Smart India Hackathon 2026**

Last Updated: October 5, 2026
