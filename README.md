# 📱 Phone Heading (Compass) Web App

A **minimal, single-file web app** that shows your phone's heading (North–South–East–West) using the built-in motion and orientation sensors. Works directly in the browser — no installation or backend required.

🌐 **Live demo:** [https://petervschp.github.io/mvp-phone_compass/](https://petervschp.github.io/mvp-phone_compass/)

---

## 🚀 Features

* **Real-time compass** showing direction (N, NE, E, …) and degrees (0–360°)
* **Responsive needle** with smooth rotation
* **iOS & Android support** (handles both `webkitCompassHeading` and `alpha`)
* **Automatic screen-rotation compensation**
* **Permission request** for iOS motion sensors
* **Pure HTML, CSS, JS** — no dependencies or build tools
* **Works offline when cached (optional PWA setup)**

---

## 📁 Project structure

```
📦 phone-heading
 ├── index.html      # single-file web app (HTML + CSS + JS)
 └── README.md        # documentation (this file)
```

---

## 🧭 How it works

The app listens to the browser's **DeviceOrientation** events:

```js
window.addEventListener('deviceorientation', handler, true);
```

It converts the `alpha` angle (rotation around the Z-axis) or `webkitCompassHeading` (on iOS) to a heading between 0° and 360°. The result is displayed both as a compass needle and as text (`N`, `NE`, `E`, etc.).

A lightweight rotation compensation is applied based on the current screen orientation.

---

## ⚙️ Deployment on GitHub Pages

1. Create a new repository, e.g. `phone-heading`.
2. Add the file `index.html` to the repo.
3. Commit and push to your `main` branch.
4. Go to **Settings → Pages → Build and deployment**.
5. Choose:

   * **Source:** Deploy from branch
   * **Branch:** `main` → `/ (root)`
6. After publishing, open:
   `https://<your-username>.github.io/phone-heading/`

---

## 🧩 Optional: make it a PWA

To make the app installable and work offline, add:

* a `manifest.json` file (name, icons, start URL)
* a `service-worker.js` for caching
* the appropriate `<link rel="manifest">` in `index.html`

Example manifest snippet:

```json
{
  "name": "Phone Heading",
  "short_name": "Compass",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#0b1020",
  "theme_color": "#7aa2ff",
  "icons": [
    { "src": "icon-192.png", "sizes": "192x192", "type": "image/png" },
    { "src": "icon-512.png", "sizes": "512x512", "type": "image/png" }
  ]
}
```

---

## 🧠 Troubleshooting

| Issue                        | Cause                                       | Fix                                          |
| ---------------------------- | ------------------------------------------- | -------------------------------------------- |
| ❌ “Permission denied” on iOS | iOS 13+ requires explicit user permission   | Tap **Enable Compass** → allow motion access |
| ❌ No movement detected       | Device or browser lacks orientation sensors | Test on a real phone (not laptop/desktop)    |
| ❌ Heading looks wrong        | Magnetic calibration off                    | Move phone in a “figure-8” motion            |

---

## 📜 License

MIT License — free to use, modify, and share.

---

## 💡 Credits

Developed as an educational MVP example of the **DeviceOrientation API** and **mobile web sensors**.

Author: Peter V
