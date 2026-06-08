# 🏗 Construction Materials Manager

A full-featured **construction site inventory system** built as a single, zero-dependency HTML file. No npm, no build step, no server — just download and open in any browser.

![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react)
![Java](https://img.shields.io/badge/Java-Backend-ED8B00?style=flat-square&logo=openjdk)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

---

## ✨ Features

### 📊 Dashboard
- Live inventory value totals and category breakdown
- SVG bar chart of stock value per category
- Recent activity feed
- Low-stock alerts panel

### 📦 Materials
- Full CRUD — add, edit, delete materials
- 10 categories: Cement, Steel, Wood, Brick, Aggregate, Paint, Plumbing, Electrical, Insulation, Other
- 9 unit types: KG, TON, Liter, Meter, m², m³, Unit, Bag, Roll
- Search by name or supplier, filter by category
- Low-stock status badge with visual alert
- **Export to CSV**

### 🔄 Stock Operations
- **Stock In** — receive materials with purchase price and PO reference
- **Stock Out** — consume materials, assign to project/site
- **Adjust** — set exact quantity after physical count
- Real-time warning when stock falls below minimum level

### 📋 Transactions
- Complete audit trail of every stock movement
- Filter by type (Stock In / Stock Out / Adjustment)
- Search by material name or notes
- **Export to CSV**

### 📄 Purchase Orders
- Create POs with multiple line items per supplier
- **Receive** a PO → automatically triggers Stock In for all items
- Cancel POs
- Status tracking: Pending / Received / Cancelled

### 🏗 Projects
- Create job sites with name, location, and material budget
- Log material usage directly against a project — deducts from stock automatically
- Budget progress bar (turns amber at 70%, red at 90%)
- Per-project material cost tracking and usage log
- **Export project usage report to CSV**

### 🏭 Suppliers
- Auto-populated from your materials inventory
- Add contact details: person, phone, email, address, payment terms
- Each card shows: materials supplied, total stock value, PO count
- **Export supplier directory to CSV**

### 🤖 AI Assistant
- Chat interface powered by the Anthropic API
- Live inventory context injected automatically — the AI knows exactly what you have in stock
- Quick prompts: reorder recommendations, cost analysis, procurement plan
- Requires your own Anthropic API key (entered in the UI, never stored)

### 📈 Reports
- SVG donut chart of inventory value distribution
- Top 5 materials by value with progress bars
- Category breakdown table
- Low-stock deficit report

---

## 🚀 Getting Started

### Option 1 — Just open it
```
1. Download construction-materials-manager.html
2. Double-click to open in your browser
3. Done.
```

### Option 2 — Serve locally (optional)
```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 18 (UMD, no build step) |
| Charts | Hand-built SVG — zero charting libraries |
| Persistence | `localStorage` — data survives page refresh |
| AI | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Styling | CSS custom properties, dark mode via `prefers-color-scheme` |
| Backend | Java 17+ (separate module — see `/src`) |

---

## ☕ Java Backend

The `src/` directory contains a full Java console application that mirrors the frontend's features:

```
src/
├── Main.java                  ← CLI entry point + menus
├── model/
│   ├── Material.java          ← Material entity
│   └── Transaction.java       ← Stock movement record
├── service/
│   └── MaterialService.java   ← Business logic & in-memory data
└── ui/
    └── ConsoleUI.java         ← ANSI-colored console output
```

### Compile & run
```bash
cd src
find . -name "*.java" | xargs javac -d ../out
cd ../out && java Main
```

Requires **Java 17+**.

---

## 🤖 AI Assistant Setup

1. Get a free API key at [console.anthropic.com](https://console.anthropic.com)
2. Open the app → click **AI assistant** tab
3. Paste your key in the field (stored in memory only, never saved to disk)
4. Ask anything about your inventory

---

## 📁 Project Structure

```
construction-materials-app/
├── construction-materials-manager.html   ← Complete frontend (single file)
├── src/                                  ← Java backend source
│   ├── Main.java
│   ├── model/
│   ├── service/
│   └── ui/
└── README.md
```

---

## 🗺 Roadmap

- [ ] Connect frontend to Java Spring Boot REST API
- [ ] PostgreSQL / SQLite persistence layer
- [ ] JWT authentication and multi-user support
- [ ] Material usage forecasting based on consumption history
- [ ] PDF report generation
- [ ] Mobile-optimised layout

---

## 👨‍💻 Author

**Rodrigo Ramires** — Java Back-End Developer  
[github.com/ramiresrodrigodev](https://github.com/ramiresrodrigodev)

---

## 📄 License

MIT — free to use, modify, and distribute.
