# ARC INTEL - Arc Raiders Daily Tips Aggregator

A static website that aggregates tips, guides, meta builds, and community strategies for Arc Raiders from multiple sources. Updated automatically every 24 hours via GitHub Actions.

![Screenshot](https://img.shields.io/badge/Updated-Daily-brightgreen) ![License](https://img.shields.io/badge/License-MIT-blue)

## Features

- 🔄 **Daily Updates**: Automatically scrapes fresh content every day at 6 AM UTC
- 📊 **Multi-Source Aggregation**: Pulls from Reddit, Steam Discussions, and curated community tips
- 🏷️ **Smart Tagging**: Auto-categorizes tips into Weapons, Builds, Maps, PvP, PvE, and Meta
- 🔥 **Hot Tips**: Highlights trending and high-engagement content
- 📱 **Responsive Design**: Works on desktop and mobile
- ⚡ **Static & Fast**: No backend required, loads instantly

## Sources

- **r/ArcRaiders** - Reddit community (hot, new, and top posts)
- **Steam Discussions** - Official game forums
- **Community Curated** - Hand-picked verified tips from veteran players
- **Patch Notes** - Official balance changes and meta shifts

## Local Development

### Prerequisites

- Python 3.11+
- A modern web browser

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/arc-raiders-tips.git
cd arc-raiders-tips
```

2. Run the scraper to populate data:
```bash
python scraper.py
```

3. Serve the site locally:
```bash
python -m http.server 8000
```

4. Open http://localhost:8000 in your browser

## Deployment

### GitHub Pages

1. Push to GitHub
2. Go to Settings → Pages
3. Set source to "Deploy from a branch"
4. Select `main` branch and `/ (root)` folder
5. Your site will be live at `https://yourusername.github.io/arc-raiders-tips`

### Netlify

1. Connect your GitHub repository
2. Build command: `python scraper.py`
3. Publish directory: `/`
4. Deploy!

### Vercel

1. Import from GitHub
2. Framework: Other
3. Build command: `python scraper.py`
4. Output directory: `.`

## Project Structure

```
arc-raiders-tips/
├── index.html              # Main website
├── scraper.py              # Python scraper script
├── data/
│   ├── tips.json           # Aggregated tips data
│   └── builds.json         # Meta builds data
├── .github/
│   └── workflows/
│       └── scrape.yml      # Daily GitHub Actions workflow
└── README.md
```

## Data Format

### tips.json

```json
[
  {
    "id": "abc123def456",
    "title": "Tip title here",
    "content": "Detailed tip content...",
    "tags": ["weapons", "meta"],
    "source": "r/ArcRaiders",
    "url": "https://reddit.com/r/ArcRaiders/...",
    "score": 150,
    "scraped_at": "2025-01-19T12:00:00",
    "isNew": true,
    "hot": false
  }
]
```

### builds.json

```json
[
  {
    "name": "PvP Assault",
    "type": "PvP",
    "primary": "Tempest",
    "secondary": "Stitcher",
    "sidearm": "Any Pistol",
    "augment": "Combat Mk.3",
    "skills": {
      "mobility": 45,
      "conditioning": 20,
      "survival": 10
    },
    "notes": "Build strategy notes..."
  }
]
```

## Customization

### Adding New Sources

Edit `scraper.py` and add a new scraping function:

```python
def scrape_new_source() -> list[Tip]:
    tips = []
    # Your scraping logic here
    return tips
```

Then add it to the `main()` function.

### Modifying Tags

Edit the `extract_tags()` function in `scraper.py` to add new tag categories or keywords.

### Styling

All styles are in the `<style>` block of `index.html`. Key CSS variables:

```css
:root {
    --accent-orange: #ff6b35;
    --accent-cyan: #00d4ff;
    --bg-primary: #0a0a0c;
    /* ... */
}
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-source`)
3. Commit your changes (`git commit -am 'Add new source'`)
4. Push to the branch (`git push origin feature/new-source`)
5. Open a Pull Request

## Disclaimer

This is a community project and is not affiliated with Embark Studios or Arc Raiders. All game content belongs to their respective owners.

## License

MIT License - feel free to use and modify for your own projects.
