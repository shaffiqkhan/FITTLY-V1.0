# FITTLY: AI-Powered Digital Tailoring & Contactless Body Measurement Studio

[![License: MIT](https://img.shields.io/badge/License-MIT-emerald.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-19.0.0-61dafb.svg)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-blue.svg)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38bdf8.svg)](https://tailwindcss.com/)

FITTLY is a contactless body measurement and digital tailoring platform. It leverages multi-modal computer vision to extract anatomical keypoints from front and side photos, computes accurate physical dimensions and circumferences, allows real-time interactive tailoring on a vector canvas, and delivers web-grounded garment size recommendations for retail e-commerce.

---

## 🌐 Live Interactive Web Application

Experience the live system directly in your browser:

👉 **[Launch FITTLY Live Web App](https://ais-pre-h55d2b7ium6bzdnoe47cpo-587725839219.asia-southeast1.run.app)**

*The live app is hosted on Google Cloud Run and runs with an active server-side AI proxy, so you can test body measurement extraction and size recommendations immediately.*

---

## 🎥 Walkthrough Video Demonstration

A 30-second walkthrough video demonstrating the entire workflow (uploading photos, anatomical keypoint detection, real-time tailoring adjustments, and custom profile export) is included in this repository:

👉 **Video File:** [docs/demo-walkthrough.mp4](docs/demo-walkthrough.mp4)

### Core Workflow Highlighted in the Video:
1. **Pose Capture & Scanning:** Uploading front and profile photographs with standard calibration.
2. **Keypoint & Biometric Extraction:** Identifying 18 frontal landmarks and 9 profile landmarks with circumference approximation.
3. **Interactive Digital Tailoring:** Drag-and-drop vector nodes on custom garments with real-time Euclidean distance scaling.
4. **Smart Apparel Sizing:** Web-grounded size chart scraping and automated fit recommendation.

---

## ✨ Key Features

- **Contactless Anatomical Scanning:** Multi-point landmark detection from standard smartphone or webcam photos.
- **Accurate Biometric Approximation:** Calculates chest, waist, hips, inseam, shoulder width, and sleeve lengths with unit switching (centimeters & inches).
- **Interactive 2D/3D Tailoring Canvas:** Real-time geometric manipulation of garment patterns with immediate pattern measurements and tolerance bounds.
- **Web-Grounded Smart Shopping:** Paste any apparel product URL to extract its official size chart and receive personalized size recommendations.
- **Secure Server-Side Architecture:** Production-ready Express microservice hosting all AI model calls behind a protected proxy route.
- **100% Client-Side Privacy Fallback:** LocalStorage persistence for user measurement profiles without requiring external database accounts.

---

## 🏛️ System Architecture

```
[ Browser / Mobile Client ] 
        │
        │ HTTP / JSON (Keypoints, Custom Measurements, Store URLs)
        ▼
[ Node.js + Express Server Proxy ]  ── (process.env.GEMINI_API_KEY)
        │
        │ Google GenAI SDK (@google/genai)
        ▼
[ Gemini Vision & Reasoning Engine ] ── (Grounding & Structured Schema Extraction)
```

- **Frontend:** React 19, TypeScript, Tailwind CSS v4, Lucide Icons, Framer Motion.
- **Backend:** Node.js 20, Express, `@google/genai` TypeScript SDK.
- **Packaging:** Full-stack unified server (`server.ts`) serving Vite middleware in development and pre-compiled static bundles in production.

---

## 🚀 Quick Start & Installation

### Prerequisites
- **Node.js** >= 18.0.0
- **npm** >= 9.0.0
- A **Google Gemini API Key** (available from [Google AI Studio](https://aistudio.google.com/))

### 1. Clone the Repository
```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd FITTLY
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the project root:
```bash
cp .env.example .env
```

Add your API key inside `.env`:
```env
GEMINI_API_KEY=your_actual_gemini_api_key_here
PORT=3000
```

### 4. Start Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### 5. Build for Production
```bash
npm run build
npm start
```

---

## 📁 Repository Structure

```
├── docs/
│   └── demo-walkthrough.mp4    # 30-second workflow demonstration video
├── src/
│   ├── components/             # Reusable UI widgets and modals
│   ├── lib/                    # Client API adapters and utilities
│   ├── App.tsx                 # Core application controller and navigation
│   ├── main.tsx                # Client entry point
│   └── index.css               # Tailwind CSS stylesheet
├── scripts/
│   └── create_walkthrough_video.py # Reproducible video generator
├── server.ts                   # Express backend & AI proxy server
├── package.json                # Project dependencies and scripts
├── tsconfig.json               # TypeScript configuration
├── vite.config.ts              # Vite bundler configuration
└── LICENSE                     # MIT License
```

---

## 🧪 Verification & Quality Checks

Run the automated test and compilation checks:

```bash
# Type check and syntax validation
npm run lint

# Compile production bundle
npm run build
```

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
