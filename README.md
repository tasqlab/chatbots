# Chatbots Collection

A collection of web-based AI chatbot interfaces powered by Groq's fast LLM inference.

## Overview

This repository contains three distinct chatbot UIs, all connected to Groq's API via a Cloudflare Worker proxy:

| Chatbot | Style | Features |
|---------|-------|----------|
| **Velocity AI** | Elegant, premium UI | Model selection, chat history, themes, export |
| **Hackibot** | Cyberpunk terminal | Retro CRT effects, markdown rendering |
| **MonkeyGPT** | Minimalist | Typewriter streaming effect, clean mono aesthetic |

## Architecture

All chatbots route requests through a Cloudflare Worker:

```
┌─────────────┐     ┌─────────────────────────────┐     ┌──────────┐
│  Chatbot UI │────▶│  velocity-groq-proxy.worker │────▶│ Groq API │
└─────────────┘     └─────────────────────────────┘     └──────────┘
```

**Worker URL:** `https://velocity-groq-proxy.tchazq1n.workers.dev`

The worker handles:
- API authentication (key stored securely in worker)
- CORS headers for browser requests
- Request/response proxying

## Available Models

- `openai/gpt-oss-120b` - OpenAI's 120B parameter model (recommended)
- `llama-3.3-70b-versatile` - Meta's Llama 3.3 70B
- `qwen/qwen3-32b` - Alibaba's Qwen3 32B
- `llama-3.1-8b-instant` - Fast 8B model

## Usage

1. Open `index.html` in a browser
2. Click any chatbot card
3. Start chatting immediately (no API key needed)

## Local Development

All chatbots are static HTML files. Serve with any static server:

```bash
# Python
python -m http.server 8080

# Node.js (npx)
npx serve .

# PHP
php -S localhost:8080
```

Then open `http://localhost:8080`

## File Structure

```
chatbots/
├── index.html        # Landing page with all chatbots
├── velocitychat.html # Premium chat interface
├── hackibot.html     # Terminal/cyberpunk UI
├── monkeygpt.html    # Minimalist mono UI
└── README.md
```

## License

Open source - feel free to modify and distribute.
