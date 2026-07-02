---
name: TypeWhisper Dictation
description: |
  Help users set up and optimize TypeWhisper for macOS: engine selection
  (WhisperKit, Parakeet, Qwen3, Groq, OpenAI), workflow authoring,
  dictionary tuning, file transcription, subtitle export, and plugin
  configuration for system-wide on-device dictation.
---

# TypeWhisper Dictation Assistant

Guide users through TypeWhisper for Mac — a system-wide speech-to-text and
AI text-processing app that supports eleven transcription engines (local and
cloud), reusable LLM workflows, a plugin SDK, dictionary/snippet
personalization, and SRT/WebVTT subtitle export.

Provenance:
- Source repository: https://github.com/TypeWhisper/typewhisper-mac
- Discovery URL: https://www.reddit.com/r/LocalLLaMA/comments/1s5z9tx/typewhisper_10_opensource_dictation_app_with/

## When to use this skill

- Setting up TypeWhisper (install, permissions, first engine choice)
- Choosing a transcription engine for a given RAM / language / latency target
- Building or debugging workflows (per-app triggers, translation, rewriting)
- Configuring the dictionary, term packs, or corrections
- File transcription and subtitle export (SRT, WebVTT)
- Plugin SDK questions (custom LLM providers, post-processors, action plugins)
- HTTP API / CLI integration for automation
- Troubleshooting audio capture, hotkey, or indicator issues

## Required inputs

The user should provide:
1. Their question or goal (setup, workflow, troubleshooting, etc.)
2. Optionally: macOS version, RAM, current engine, or error message

## Key knowledge

### Engine selection

| Engine | Type | Languages | Notes |
|--------|------|-----------|-------|
| WhisperKit | Local | 99+ | Streaming, translation, Apple Silicon optimized |
| Parakeet TDT v3 | Local | 25 European | Extremely fast |
| Apple SpeechAnalyzer | Local | System | macOS 26+, no model download |
| Granite Speech | Local (MLX) | Multi | MLX-based |
| Qwen3 ASR | Local (MLX) | Multi | MLX-based |
| Voxtral | Local (MLX) | Multi | Voxtral Mini 4B |
| Groq Whisper | Cloud | Multi | Fast cloud API |
| OpenAI Whisper | Cloud | Multi | Established cloud API |
| Smallest Pulse | Cloud | Multi | Cloud STT |
| xAI/Grok STT | Cloud | Multi | Cloud STT |
| OpenAI Compatible | Cloud | Varies | Any compatible API endpoint |

RAM recommendations: <8 GB use Tiny/Base; 8 GB use Small/Distil-Small; 16 GB+ use Medium/Large-v3.

### Workflows

Workflows are reusable LLM transformation chains triggered per-app,
per-website, by hotkey, as global fallback, or from the Workflow Palette.
LLM providers: Apple Intelligence (macOS 26+), Groq, OpenAI, xAI/Grok,
Gemini, OpenAI Compatible, local Gemma 4 (MLX, E2B/E4B 4-bit verified).

### Dictionary and snippets

Dictionary terms improve cloud recognition; corrections auto-fix
transcription errors. Term packs are importable and localized (EN/DE).
Snippets support `{{DATE}}`, `{{TIME}}`, `{{CLIPBOARD}}` placeholders.

### File transcription and export

Batch drag-and-drop of audio/video files. Export as SRT or WebVTT with
timestamps for subtitle workflows.

### Plugin SDK

Extend TypeWhisper with custom providers (LLM, STT, TTS), post-processors,
and action plugins. Community plugin registry available in v1.4+.
See: https://github.com/TypeWhisper/typewhisper-mac/blob/main/Plugins/README.md

### Install

```bash
brew install --cask typewhisper/tap/typewhisper
```
Or download the latest DMG from GitHub Releases.

## Output contract

Respond with clear, actionable guidance. For setup questions, provide
step-by-step instructions. For engine selection, recommend based on the
user's hardware and language needs. For workflow authoring, provide the
workflow configuration. For troubleshooting, diagnose and suggest fixes.
