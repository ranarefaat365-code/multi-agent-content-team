# Multi-Agent Content Team

A Streamlit app where a team of five specialized AI agents collaborate to
produce content. Give it a topic, content type, audience, and tone, and the
team plans, researches, writes, edits, and quality-checks the result — each
agent handing its output to the next.

## What is a multi-agent system?

Instead of one agent doing everything, a multi-agent system splits the work
across specialized agents, each with a focused role. Specialization improves
quality — just like a real content team with a planner, researcher, writer,
editor, and reviewer.

## The team

```
topic → Planner → Researcher → Writer → Editor → QA → final content
```

Each agent's output becomes the next agent's input, coordinated through a
shared state object.

## Features

- **Five specialized agents** — Planner, Researcher, Writer, Editor, QA.
- **Handoff workflow** — each agent builds on the previous agent's output.
- **Shared state** — a state object carries every agent's output through the pipeline.
- **Configurable** — choose content type, audience, and tone.
- **Transparent** — each agent's output is shown in its own tab, with step logging.
- **Saved output** — the final content is saved as a timestamped Markdown file.

## Project structure

| File | Job |
|------|-----|
| `app.py` | The Streamlit UI (inputs, tabs, step log) |
| `content_team.py` | The ContentTeam class that orchestrates the five agents |
| `agent_prompts.py` | The prompt (role) for each agent |
| `knowledge_tool.py` | A local keyword-based search tool over sample knowledge |
| `llm_service.py` | The brain — routes messages to the chosen AI provider |
| `.env.example` | Safe template showing which settings to create |

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Copy `.env.example` to `.env` and add your real key:
   ```bash
   cp .env.example .env
   ```
3. Run the app:
   ```bash
   streamlit run app.py
   ```

## Providers

- **Gemini** (default): free API key from Google AI Studio.
- **OpenAI**: OpenAI API key.
- **Ollama**: runs a model locally, no key needed.

Switch provider by editing `LLM_PROVIDER` in `.env`.

## Note

The knowledge tool uses local sample sources, not live web search. It can be
replaced with a real search API or a RAG system later.

---

Built by **Rana Refaat** as part of a personal AI engineering learning path.
