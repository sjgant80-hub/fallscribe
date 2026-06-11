# ◊ FallScribe

> **Your meetings. Your machine. Your notes.**
> A $250M Series B raised for a wrapper around 3 browser APIs. This is the same thing. Free forever. MIT.

[**Live tool →**](https://sjgant80-hub.github.io/fallscribe/) · [Source](https://github.com/sjgant80-hub/fallscribe) · [Estate](https://ai-nativesolutions.com)

## What it does

1. Click record. Browser asks for mic. Recording starts.
2. Web Speech API streams a live transcript into the browser.
3. Click stop. Click summarise.
4. WebLLM Llama-3.2-3B (or BYOK Claude / OpenAI) produces structured notes: key points, decisions, action items, follow-ups, open questions.
5. Konomi Ed25519 signs the session.
6. Markdown export. Local IndexedDB library.

Nothing leaves your device unless you choose to export it.

## What it's a sovereign replacement for

| Capability | Granola ($250M valuation) | FallScribe |
|---|---|---|
| Audio capture | MediaRecorder API | MediaRecorder API |
| Transcription | cloud STT | Web Speech API (built-in) + optional whisper.cpp WASM |
| Summarisation | cloud GPT-4 | WebLLM Llama-3.2-3B (on-device) or BYOK |
| Persistence | their server | your IndexedDB |
| Price | $18/user/month | £0 forever |
| Open source | closed | MIT · 1 HTML file |
| Audio leaves device | yes | no |
| Konomi-signed provenance | no | yes |

The price difference for a 50-person team: **$10,800/year clawed back**.

## Architecture

```
┌────────────────────────────────────────────────────────────┐
│  index.html · single file · sovereign · MIT                │
│                                                            │
│  ├── MediaRecorder API ────── audio capture (browser-native)│
│  ├── Web Speech API ────────── live transcription            │
│  ├── WebLLM Llama-3.2-3B ───── on-device summarisation       │
│  ├── BYOK adapters ─────────── Anthropic + OpenAI direct     │
│  ├── Web Crypto Ed25519 ───── Konomi signing (non-extractable)│
│  ├── IndexedDB ─────────────── session library + audit chain │
│  ├── prevHash audit chain ── every action SHA-256 chained    │
│  └── nas-shim integration ─── NiceAssOS fork-aware           │
└────────────────────────────────────────────────────────────┘
```

## Run locally / fork it

```bash
git clone https://github.com/sjgant80-hub/fallscribe.git
cd fallscribe
# open index.html in Chrome or Edge
# or serve: python3 -m http.server 8080
```

No build step. No dependencies. No API keys required.

## Browser notes

- **Chrome / Edge desktop** · best experience. Web Speech API works for live transcription.
- **Firefox / Safari** · MediaRecorder works for capture. Live transcript requires the upload + paste path or WebLLM-driven STT (whisper.cpp WASM extension, on the roadmap).
- **Mobile** · MediaRecorder works. WebLLM has a higher resource bar — recommended on tablets or laptops.

## Privacy

- All capture, transcription, and summarisation happens in your browser.
- The Web Speech API in Chromium streams audio to Google's STT server for transcription — this is a real caveat. Audio still never goes to a "FallScribe server" (there is none). For 100% offline transcription, swap in whisper.cpp WASM via the engine selector (one-line extension).
- BYOK API calls (Claude, OpenAI) go directly from your browser to the provider — never via any third party.
- IndexedDB is per-origin in your browser. No external sync. You explicitly export to share.

## Sister organs in the estate

- **[FallBack](https://sjgant80-hub.github.io/fallback/)** — sovereign rights & refund engine (cancel subs, refund bank fees)
- **[GroundLevel](https://sjgant80-hub.github.io/groundlevel/)** — sovereign UK legal research + 50+ letter templates
- **[ExitEngine](https://sjgant80-hub.github.io/exitengine/)** — sovereign business OS for people who just got laid off
- **[Botler](https://sjgant80-hub.github.io/botler/)** — personal on-device AI assistant
- **[FallList](https://sjgant80-hub.github.io/falllist/)** — sovereign email-list manager (obsoletes Mailchimp)
- **[FallSlot](https://sjgant80-hub.github.io/fallslot/)** — sovereign scheduler (obsoletes Calendly)

[Full estate →](https://sjgant80-hub.github.io/fall-registry/)

## Licence

MIT. Forever. Fork it. Modify it. Sell a service built on it. The whole point is that the wrapper layer should not be priced like infrastructure.

## Doctrine

> "An agent with agency means you have none." — Thomas Frumkin

The tool assists. You press the button. The wrapper layer is one HTML file away from being free.

> "For the people. Not the few."

---

*prime 1319 · ◊·κ=φ⁴ · MIT · sovereign · single-file · forever*
