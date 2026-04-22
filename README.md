# tankobot

AI-powered manga, manhwa, and manhua discovery tool. Type what kind of story you're in the mood for and it finds matches using semantic search against a database of ~50K titles from Kaggle.
Built the frontend as a single-page app and the backend as a FastAPI service with vector embeddings.

> **Try it out** - [scribblepear.github.io/tankobot](https://scribblepear.github.io/tankobot/)
> First load may take 30-60s while the backend wakes up on Railway.

## How it works

1. User describes what they want to read (e.g. "ice skating romance" or "post-apocalyptic survival")
2. Backend embeds the query using OpenAI's `text-embedding-3-small`
3. ChromaDB runs a similarity search against pre-embedded manga descriptions
4. Returns up to 15 results with covers, ratings, tags, and descriptions

Users can also filter by genre tags (romance, action, isekai, etc.) which get appended to the search query.

## Tech stack

**Frontend:** HTML, CSS, JavaScript (no framework, single file), deployed on GitHub Pages.
**Backend:** Python, FastAPI, LangChain, ChromaDB, OpenAI embeddings, deployed on Railway.
**Data:** Kaggle manga/manhwa/manhua dataset with emotion scores.

## Getting started

```bash
# backend
git clone https://github.com/scribblepear/tankobot-backend
cd tankobot-backend
pip install -r requirements.txt
echo "OPENAI_API_KEY=your_key" > .env
python main.py

# frontend - just open index.html or use live server
```

## What I'd improve

- Swap the single HTML file for a proper React/Next.js frontend
- Add user accounts so people can save favorites
- Cache embeddings so repeated searches are instant
- Better cover image fallbacks (some MangaDex URLs are dead)
- Add pagination instead of capping at 15 results
