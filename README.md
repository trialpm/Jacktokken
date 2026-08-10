# 📱 SMS Bot v3

## Install & Run
```bash
pip install -r requirements.txt
python bot.py
```

---

## How It Works — Simple Flow

```
/start
  │
  ├── 🧙 Setup Wizard  ← First time? Start here
  │     Step 1/5 — Firebase URL
  │     Step 2/5 — Pick Device (fetched live)
  │     Step 3/5 — Pick SIM(s) — multi-select ✅
  │     Step 4/5 — Pick Channel
  │     Step 5/5 — Repeat count (1/2/3/custom)
  │          ↓
  │     🟢 Monitor auto-starts!
  │
  ├── ▶️ Start/Stop Monitor  ← Resume with saved combo
  ├── 📊 Dashboard           ← Live stats + active combo
  ├── ⚙️ My Settings         ← Manage Firebase / Devices / Channels
  ├── 📤 Forward             ← Add/remove forward targets
  ├── 🗑 Reset Me            ← Clear your own data
  └── 🛡 Admin Tools         ← (Admins only)
        ├── 👥 Users list
        ├── ➕ Add Timed User (1h/6h/24h/7d/custom/permanent)
        ├── 📊 Global stats
        ├── 🟢/🔴 Free Mode toggle      ← Owner only
        ├── ➕ Add Admin                ← Owner only
        ├── 📦 Export ZIP (1-click)    ← Owner only
        └── 💥 Reset ALL               ← Owner only
```

---

## Progress UI (Beautiful Cards)

Every screen shows visual progress:
- `■■■■□□□□` — block bar
- `●●●●○○○○` — round bar
- `▶▶▶▷▷` — step arrows
- Setup card shows ✅/🔲 for each step
- Stats card shows sent/failed rate with bar

---

## Owner ID Security

Owner ID is split into 4+ fragments scattered across the file:
- Fragment in struct bytes
- Fragment in unicode escapes  
- Fragment disguised as config constants
- Never stored or printed as a plain integer
- Assembled at runtime only when needed

---

## Permissions

| Feature           | Owner | Admin | Timed User |
|-------------------|-------|-------|------------|
| Use bot           | ✅    | ✅    | ✅ (while valid) |
| Setup + Monitor   | ✅    | ✅    | ✅ |
| Add Timed Users   | ✅    | ✅    | ❌ |
| Add Admin         | ✅    | ❌    | ❌ |
| Free Mode         | ✅    | ❌    | ❌ |
| Export ZIP        | ✅    | ❌    | ❌ |
| Reset ALL         | ✅    | ❌    | ❌ |
| Admin Tools btn   | ✅    | ✅    | ❌ |

---

## Hardcoded

| Role          | ID         | Visibility |
|---------------|------------|------------|
| 👑 Owner       | 7949539794 | Hidden (fragmented) |
| 🛡 Default Admin | 8720166775 | Open |
