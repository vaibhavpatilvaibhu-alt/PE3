# Product Copy Generator & Sentiment Analyzer

Render-ready FastAPI application with a simple browser UI at `/` and API docs at `/docs`.

## Deployment
1. Extract this ZIP and upload the contents (including render.yaml) to your Git repository root.
2. On Render create a Blueprint from the repository, or create a Python Web Service manually.
3. Build: `pip install -r requirements.txt`
4. Start: `uvicorn app:app --host 0.0.0.0 --port $PORT`
5. Set OPENAI_API_KEY in Render environment settings. OPENAI_MODEL defaults to gpt-4o-mini; choose a model your account can access that supports Chat Completions JSON output.
6. Open your service URL for the UI, or append /docs for API testing.

Python 3.11 or newer recommended. API generation requires an OpenAI API account with available credits and sends product data to OpenAI. Sentiment works without an API key.

## Local use
python -m venv .venv
Activate the virtual environment, then:
pip install -r requirements.txt
Copy .env.example to .env and fill in your key.
uvicorn app:app --reload
Open http://127.0.0.1:8000

## Differences from the earlier version
Uses lightweight VADER sentiment instead of PyTorch/Transformers, avoiding the large model download. Sentiment is English, lexicon-based, and may miss sarcasm or domain-specific meaning. Scores are not confidence probabilities. Combined endpoint accepts JSON {"product": {...}, "reviews": ["..."]}.

## Security and limitations
This is a demo, not a hardened public production service. It has no authentication or rate limiting. Restrict access or add both before publishing an API key-backed service publicly, to prevent unauthorized paid API use. Never commit .env. Review all generated claims. No live Render deployment or OpenAI API call has been tested for this archive. Render hosting and OpenAI API charges may apply.
