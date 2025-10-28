# Stylable Digital Timer (MM:SS.CS)

A single‑file, client‑only web timer that counts **up** or **down** to a target duration with a clean digital display. Includes a **live style preview**, color and font customization, an optional **start delay**, and an **Esc to cancel** shortcut.

> This repo contains one HTML file. No build step, no dependencies.

---

## ✨ Features
- **Count up** (00:00.00 → target) or **count down** (target → 00:00.00)
- **Live preview** box updates as you tweak colors and font
- **Start delay** (e.g. 1s) shows 00:00.00 before the run begins
- **Show centiseconds** toggle (two decimals, e.g. `08:43.12`)
- **Monospace fallback** so digits don’t “jump” during animation
- **Fixed-height display** to prevent vertical layout shifts
- **Esc** cancels the run and **restores original page styles**
- Works offline (except optional Google Fonts loading)

---

## 🎛 Controls (Form)
| Control | What it does | Default | Notes |
|---|---|---|---|
| **MM / SS / CS** | Target minutes / seconds / centiseconds | `0 / 0 / 0` | SS is clamped to **0–59**, CS to **0–99** (auto‑correct on blur and at runtime). |
| **Delay Seconds** | Wait time before the timer starts | `1` | Display remains at `00:00.00` (or target if reverse) during the delay. |
| **Background Color** | Page background | `#000000` | Applied to the whole page while running and in preview. |
| **Font Color** | Timer text color | `#ffffff` | Applied to preview and running timer. |
| **Font Family** | Monospaced font choice | `monospace` | Includes system monospace fonts and web fonts (see below). |
| **Reverse (Count Down)** | Run downwards from target to zero | `off` | Starts at target time instead of zero. |
| **Show centiseconds** | Show or hide `.CC` (centis) | `on` | When off, display shows only `MM:SS`. |

**Keyboard shortcut**: Press **Esc** any time to cancel the run and return to the form. The page’s original styles (background/text/font) are restored.

---

## 🧠 How It Works
- Uses `performance.now()` and `requestAnimationFrame` for smooth, accurate timing.
- Formats the display as `MM:SS.CC` (centiseconds = two decimal digits).
- Locks the timer/preview height via CSS (`line-height: 1; height: 1em;`) to prevent vertical jumps across fonts.
- Adds a **monospace fallback** to keep digit widths stable even if a chosen font isn’t installed.

### Web Fonts
The file preloads Google Fonts so font choices apply consistently:
- **Source Code Pro**
- **Roboto Mono**
- **Ubuntu Mono**

> If you need full offline operation with a non‑system font, consider self‑hosting the font files and removing the Google Fonts `<link>` tags.


---

## 🧩 File Layout
Just one file (you can name it `index.html`):
```
index.html   # open in a browser; no build tools required
```

---

## 🛠 Notes & Limits
- **Accuracy**: Good for display and demonstrations. Like any JS timer, it depends on the tab being active for smooth `requestAnimationFrame` updates.
- **Offline**: Works offline after first load, but Google Fonts require a network fetch unless cached. System monospace fallback is always available.
- **Accessibility**: High contrast defaults (black/white). You can choose your own colors in the form.

---

## 📝 License
MIT — do whatever you want, just keep the license. Replace with your preferred license if needed.
