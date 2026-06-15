# SushiMan

A modern Japanese restaurant landing page built with vanilla JavaScript and Vite. Features smooth scroll animations, a food catalog with category filters, and a fully responsive design.

**Live site:** [sushi.codewithxjohn.com](https://sushi.codewithxjohn.com)

## Overview

SushiMan is a single-page marketing site for a Japanese food delivery service. It showcases popular menu items, highlights trending sushi and drinks, and includes a newsletter subscription form — all wrapped in a warm cream-and-crimson aesthetic.

## Sections

| Section | Description |
|---|---|
| **Hero** | Full-bleed intro with a call-to-action, 24k+ happy customers stat, and a customer review snippet |
| **About Us** | Mission statement with the Omotenashi (Japanese hospitality) concept |
| **Popular Foods** | Filterable catalog (All / Sushi / Ramen / Udon / Danggo / Other) with ratings and prices |
| **Trending** | Side-by-side spotlights on Japanese Sushi and Japanese Drinks with item lists |
| **Subscription** | Newsletter sign-up form |
| **Footer** | Logo, navigation links, and social media icons |

## Tech Stack

- **Vite** — build tool and dev server
- **Vanilla JavaScript** — no framework
- **CSS** — modular per-section stylesheets, CSS custom properties, responsive media queries
- **AOS** (Animate On Scroll) — scroll-triggered entrance animations
- **Google Fonts** — Playfair Display (headings) + Plus Jakarta Sans (body)

## Getting Started

**Prerequisites:** Node.js 18+

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Docker

Multi-stage build: Node 20 Alpine compiles the app with Vite, then the static output is served by Nginx Alpine on port `8080`. Runs as a non-root user.

```bash
# Build image
docker build -t sushi .

# Run container
docker run -p 8080:8080 sushi
```

## Kubernetes

Kubernetes manifests are in [kubernetes/](kubernetes/). The setup uses:

- **Traefik** as the ingress controller
- **cert-manager** with Let's Encrypt for TLS
- Liveness and readiness probes on port `8080`
- Resource limits: 128Mi memory, 100m CPU

```bash
kubectl apply -f kubernetes/
```

Served at `sushi.codewithxjohn.com` and `www.sushi.codewithxjohn.com`.

## Project Structure

```
├── src/
│   ├── assets/        # Images and SVG icons
│   ├── css/
│   │   ├── sections/  # Per-section stylesheets
│   │   └── style.css  # Global styles and CSS variables
│   └── js/
│       └── script.js  # AOS initialization
├── public/            # Static assets (favicon, icons)
├── kubernetes/        # K8s deployment, service, ingress, TLS
├── Dockerfile
├── nginx.conf
└── index.html
```
