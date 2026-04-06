# ⌘ CodeForge — Random Code Generator
### Python Flask Backend + Responsive Frontend

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Run the server
python app.py

# 3. Open browser
http://127.0.0.1:5000
```

---

## 📁 Project Structure

```
codeforge/
├── app.py              ← Flask backend (Python)
├── requirements.txt    ← pip dependencies
├── README.md
└── templates/
    └── index.html      ← Full frontend (served by Flask)
```

---

## 🔐 Demo Login Accounts

| Username | Password  |
|----------|-----------|
| admin    | admin123  |
| demo     | demo123   |
| forge    | forge2024 |

---

## 🐍 Python Modules Used

| Module       | Purpose                                  |
|--------------|------------------------------------------|
| `flask`      | Web framework / routing / sessions       |
| `secrets`    | Cryptographically secure random codes    |
| `string`     | Character set constants                  |
| `uuid`       | UUID v4 generation                       |
| `base64`     | Base64 encoding                          |
| `hashlib`    | SHA-256 password hashing                 |
| `math`       | Shannon entropy calculation (log2)       |
| `time`       | CAPTCHA expiry timestamp                 |
| `datetime`   | Code generation timestamps               |

---

## 🎛️ API Endpoints

| Method | Route                | Description                    |
|--------|----------------------|--------------------------------|
| GET    | `/`                  | Serve the frontend             |
| GET    | `/api/captcha/new`   | Generate a new CAPTCHA code    |
| POST   | `/api/captcha/verify`| Verify CAPTCHA + credentials   |
| POST   | `/api/generate`      | Generate random codes          |
| POST   | `/api/logout`        | Clear session                  |
| GET    | `/api/me`            | Get current session user       |

---

## 📦 Generate API — Request Body

```json
{
  "type": "password",        // uuid|pin|hex|token|base64|alphanumeric|numeric|mnemonic
  "length": 16,              // 4–128
  "quantity": 5,             // 1–100
  "prefix": "CF-",           // optional, max 20 chars
  "upper": true,
  "lower": true,
  "numbers": true,
  "symbols": false,
  "exclude_ambiguous": false
}
```

### Response

```json
{
  "ok": true,
  "type": "password",
  "codes": [
    {
      "code": "CF-Xk9mP3qRvT2nYw",
      "entropy": 95.2,
      "strength": "Strong",
      "length": 18,
      "ts": "14:32:07"
    }
  ]
}
```

---

## ✨ Features

- **8 code types**: Password, UUID, PIN, HEX, Token, Base64, Alphanumeric, Numeric
- **Python `secrets` module** — OS-level cryptographic entropy
- **Shannon entropy** calculated server-side in bits
- **CAPTCHA** — server-generated, canvas-rendered with distortion
- **Batch generation** — up to 100 codes per request
- **Fully responsive** — mobile, tablet, desktop
- **Animated UI** — particle canvas, scroll reveals, custom cursor
- **History table** — session tracking with entropy scores
- **Export** — copy all or download as `.txt`
