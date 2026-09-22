# Fake ID Screening

[![CI](https://github.com/rajaryan1111/fake-id-screening/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/rajaryan1111/fake-id-screening/actions/workflows/ci.yml)

AI-assisted identity and document screening platform for flagging potentially suspicious identity documents for human review.

## Overview

The project combines document-image analysis, OCR, backend APIs and a mobile-camera workflow. The repository is structured as a modular screening system so the detection components can evolve independently from the client experience.

## Current capabilities

- **Document screening API** — FastAPI endpoint for submitting a document image and a live photo.
- **Input validation** — MIME-type and file-size validation, with a 10 MB upload limit.
- **Safe file handling** — UUID-based filenames to avoid traversal and predictable-file enumeration.
- **Database layer** — Supabase PostgreSQL integration through SQLAlchemy, with a students model and development seed data.
- **Mobile capture flow** — camera-based capture workflow for the screening experience.
- **Offline demo mode** — supports demonstration of verification flows without depending on a deployed backend.

## Architecture

~~~text
Mobile Camera
     │
     ▼
Document + Live Photo
     │
     ▼
Screening API (FastAPI)
     │
     ├── Input validation
     ├── OCR / image-analysis modules
     └── Screening result
             │
             ▼
      PostgreSQL / Supabase
~~~

## API

Health check:

~~~text
GET /health
~~~

Screening:

~~~text
POST /api/v1/screen
~~~

The screening endpoint accepts a document image and live photo, validates the request, and stores uploaded files using unique UUID filenames.

## Repository goals

The project is intended as a practical prototype for identity-document screening rather than an authoritative identity-verification service. Detection results should be treated as signals for human review.

## Development

The codebase is intentionally separated into client, backend and screening components so individual detection modules can be tested or replaced without rewriting the complete workflow.

## Disclaimer

This project is a prototype. It does not establish whether a real identity document is genuine or fraudulent with legal certainty; results require appropriate human review.


---

**Project documentation:** [Contributing](CONTRIBUTING.md) · [Security](SECURITY.md)
