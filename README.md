<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8"/>
  <meta name="viewport" content="width=device-width,initial-scale=1"/>
  <title>🎬 Netflix Titles — README</title>
  <style>
    :root{
      --bg:#071028; --card:#0f1724; --muted:#9aa6b2; --text:#e6eef6;
      --accent:#e50914; --accent2:#00b4d8; --radius:12px; --shadow: 0 8px 28px rgba(0,0,0,.6);
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box}
    body{margin:0; background:linear-gradient(180deg,#041226 0%,var(--bg) 100%); color:var(--text); line-height:1.6}
    header{padding:48px 20px 28px; text-align:center; border-bottom:1px solid rgba(255,255,255,.03)}
    h1{margin:0; font-size:36px; letter-spacing:0.2px}
    p.lead{color:var(--muted); margin:8px auto 0; max-width:880px}
    main{max-width:980px; margin:30px auto; padding:0 18px}
    section{background:linear-gradient(180deg, rgba(255,255,255,.02), rgba(255,255,255,.01)); border:1px solid rgba(255,255,255,.03); padding:18px; border-radius:var(--radius); box-shadow:var(--shadow); margin-bottom:16px}
    h2{margin:0 0 10px; font-size:20px}
    ul{margin:8px 0 0 20px}
    pre{background:#07182b; padding:12px; border-radius:8px; overflow:auto; color:#dbeafe}
    code{background:#07182b; padding:2px 6px; border-radius:6px}
    .grid{display:grid; gap:12px}
    @media(min-width:860px){ .grid.cols-2{grid-template-columns:1fr 1fr} }
    .pill{display:inline-block; padding:6px 10px; border-radius:999px; background:rgba(255,255,255,.03); color:var(--muted); font-size:13px; border:1px solid rgba(255,255,255,.02)}
    .badges{margin-top:12px; display:flex; gap:8px; justify-content:center; flex-wrap:wrap}
    footer{color:var(--muted); text-align:center; padding:14px 0 34px}
    a { color: var(--accent2); text-decoration: none }
    a:hover{text-decoration: underline}
  </style>
</head>
<body>
  <header>
    <h1>🎬 Netflix Titles — Data & Insights</h1>
    <p class="lead">A curated dataset and analytics project for Netflix titles (movies & TV shows). Use it to explore release trends, genres, cast, ratings distribution, and regional availability.</p>
    <div class="badges">
      <span class="pill">CSV / JSON</span>
      <span class="pill">Python (pandas)</span>
      <span class="pill">SQL</span>
      <span class="pill">Power BI / Tableau</span>
    </div>
  </header>

  <main>
    <section>
      <h2>📌 Overview</h2>
      <p>
        This repository contains cleaned Netflix titles data (movies & TV shows) suitable for exploration and visualization.
        It focuses on temporal trends, genre analysis, cast & crew insights, country availability, and user-centric metrics.
      </p>
    </section>

    <section>
      <h2>📂 Project Structure</h2>
      <pre><code>netflix-titles/
├─ data/
│  ├─ raw/                     # raw CSV/JSON dumps
│  └─ processed/               # cleaned datasets (CSV/Parquet)
├─ notebooks/
│  └─ netflix_eda.ipynb        # EDA and preprocessing
├─ sql/
│  └─ analysis.sql             # useful queries / views
├─ visuals/
│  └─ screenshots/             # dashboard images / GIFs
├─ dashboards/
│  └─ netflix_dashboard.pbix   # Power BI file (optional)
└─ README.html                 # this file
</code></pre>
    </section>

    <section class="grid cols-2">
      <div>
        <h2>🧾 Dataset (Suggested Columns)</h2>
        <ul>
          <li><code>show_id</code>, <code>title</code>, <code>type</code> (Movie/TV Show)</li>
          <li><code>director</code>, <code>cast</code>, <code>country</code>, <code>date_added</code></li>
          <li><code>release_year</code>, <code>rating</code>, <code>duration</code>, <code>listed_in</code> (genres)</li>
          <li><code>description</code>, <code>imdb_score</code> (if available)</li>
        </ul>
      </div>
      <div>
        <h2>✨ Features & Analyses</h2>
        <ul>
          <li>Trends: Titles added per year / month</li>
          <li>Genre heatmap: Popular genres by region</li>
          <li>Cast network: Frequent collaborators & top actors</li>
          <li>Ratings analysis: Distribution by genre & year</li>
          <li>Content availability: Titles per country / region</li>
        </ul>
      </div>
    </section>

    <section>
      <h2>🚀 Quick Start</h2>
      <ol>
        <li>Clone the repo:<br><code>git clone https://github.com/your-username/netflix-titles.git</code></li>
        <li>Copy raw data into <code>data/raw/</code> (CSV or JSON).</li>
        <li>Run the cleaning notebook or script to produce <code>data/processed/titles.csv</code>.</li>
        <li>Open the notebook for EDA or open the PBIX file to view dashboard.</li>
      </ol>
    </section>

    <section class="grid cols-2">
      <div>
        <h2>🛠️ Example Python (pandas) Snippet</h2>
        <pre><code>import pandas as pd

df = pd.read_csv("data/raw/netflix_titles.csv", parse_dates=["date_added"])
# split genres
df["genres"] = df["listed_in"].str.split(", ").fillna(["Unknown"])
df["year_added"] = df["date_added"].dt.year
# save cleaned version
df.to_csv("data/processed/titles_clean.csv", index=False)</code></pre>
      </div>
      <div>
        <h2>🔎 Example SQL Queries</h2>
        <pre><code>-- Top genres by number of titles
SELECT genre, COUNT(*) AS cnt
FROM titles_genres
GROUP BY genre
ORDER BY cnt DESC;

-- Titles added per year
SELECT EXTRACT(YEAR FROM date_added) AS year, COUNT(*) AS added
FROM titles
GROUP BY year
ORDER BY year;</code></pre>
      </div>
    </section>

    <section>
      <h2>📊 Suggested Visuals</h2>
      <ul>
        <li>Timeseries: Titles added per month (area chart)</li>
        <li>Bar: Top 20 directors / actors by title count</li>
        <li>Treemap: Genre share of catalogue</li>
        <li>Map: Titles available per country</li>
        <li>Network: Cast co-occurrence graph (network chart)</li>
      </ul>
    </section>

    <section class="grid cols-2">
      <div>
        <h2>🤝 Contributing</h2>
        <p>Contributions welcome — open an issue or PR. Suggestions:</p>
        <ul>
          <li>Improve data cleaning & fill missing metadata</li>
          <li>Add enrichment (IMDB/TMDB ratings, genres mapping)</li>
          <li>Add reproducible dashboards & notebook explanations</li>
        </ul>
      </div>
      <div>
        <h2>📄 License & Contact</h2>
        <p>MIT License — use for learning and portfolio purposes. Add a proper data source attribution if required.</p>
        <p>Created by &lt;Your Name&gt; — <a href="mailto:you@example.com">you@example.com</a></p>
      </div>
    </section>

    <section>
      <h2>📎 Notes & Data Sources</h2>
      <p>Always verify licensing and usage terms for any scraped or third-party data. Common sources: Kaggle Netflix dataset, TMDB / OMDB for enrichment.</p>
    </section>

    <footer>
      <p>Made with ❤️ — replace the placeholders and add screenshots/GIFs in <code>visuals/screenshots/</code>.</p>
    </footer>
  </main>
</body>
</html>
