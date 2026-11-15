# 🌊 DEEP BLUE: ABYSS EXPLORER

<div align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-3D-black?style=for-the-badge&logo=three.js&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-Rendered-990000?style=for-the-badge&logo=webgl&logoColor=white)
![Single File](https://img.shields.io/badge/Single_File-HTML-4CAF50?style=for-the-badge)
![Offline](https://img.shields.io/badge/Works-Offline-22C55E?style=for-the-badge)
![Mobile Ready](https://img.shields.io/badge/Mobile-Landscape-8B5CF6?style=for-the-badge)
![Autosave](https://img.shields.io/badge/Save-LocalStorage-FFA500?style=for-the-badge)

**Dive into the abyss. Explore. Collect. Survive.**

*A browser-based 3D underwater exploration game — zero install, zero dependencies*

[🚀 How to Play](#-how-to-play) • [🎮 Controls](#-controls) • [✨ Features](#-features) • [🏗️ Architecture](#️-architecture) • [💾 Progress](#-progress--saving)

</div>

---

## 📖 Overview

**DEEP BLUE: ABYSS EXPLORER** is a **browser-based 3D underwater exploration game**.

### Core Idea

> **The deeper you go, the darker it gets.**
>
> Explore the abyss, collect what you find, upgrade your gear, and sell your haul at the boat.

### The Dive Loop

```mermaid
flowchart LR
    Dive["🤿 Dive<br/>from the boat"] --> Explore["🧭 Explore<br/>the abyss"]
    Explore --> Collect["🎣 Collect<br/>with harpoon / E"]
    Explore --> Scan["🔍 Scan<br/>with E"]
    Explore --> Light["🔦 Flashlight<br/>F"]
    Collect --> Surface["⬆️ Surface<br/>return to the boat"]
    Scan --> Journal["📓 Journal<br/>records discoveries"]
    Surface --> Sell["💰 Sell<br/>at the boat (1–5)"]
    Sell --> Upgrade["⬆️ Upgrade<br/>gear & equipment"]
    Upgrade --> Dive
    Journal --> Progress["💾 Auto-save"]
    Upgrade --> Progress

    style Dive fill:#61DAFB,color:#000
    style Explore fill:#0EA5E9,color:#fff
    style Collect fill:#22C55E,color:#fff
    style Scan fill:#8B5CF6,color:#fff
    style Light fill:#FFD700,color:#000
    style Surface fill:#FFB454,color:#000
    style Sell fill:#FF6B6B,color:#fff
    style Upgrade fill:#0f3460,color:#fff
    style Journal fill:#FF3F9E,color:#fff
    style Progress fill:#316192,color:#fff
```

---

## 🚀 How to Play

### 💻 Desktop

1. **Unzip the folder**
2. **Double-click `index.html`** in any modern browser:
   - Chrome
   - Edge
   - Firefox
   - Safari

> ✅ **Works offline.**

### 📱 Phone / Tablet

1. **Host the folder anywhere** — or
2. **Open it in a file manager that supports HTML**
3. **Rotate to landscape**

> 💡 **The game is designed for landscape orientation on mobile.**

---

## 🎮 Controls

### 🖥️ Desktop

<div align="center">

| Key | Action |
|:---:|--------|
| **W A S D** | Move |
| **Mouse** | Look |
| **Space** | Up |
| **Ctrl / C** *(or Down)* | Down |
| **Shift** | Fast |
| **E** | Interact / Collect / Scan / Sell |
| **F** | Flashlight |
| **Q** | Harpoon |
| **Tab** | Inventory + Journal |
| **M** | Map |
| **Esc** | Pause |
| **1–5** | Shop at the boat |

</div>

### 📱 Touch

<div align="center">

| Control | Action |
|:-------:|--------|
| **Left stick** | Move |
| **Drag screen** | Look |
| **Up / Down buttons** | Ascend / Descend |
| **Sprint toggle** | Fast movement |
| **E, Light, Harpoon buttons** | Actions |
| **Tap shop items** | Buy |

</div>

---

## ✨ Features

<div align="center">

| 🌊 3D Underwater World | 🧭 Free Exploration |
|:---:|:---:|
| Dive into the abyss from your boat | Explore at your own pace in any direction |
| **🎣 Collection System** | **🔦 Flashlight** |
| Harpoon targets and E to interact | Navigate the darker depths |
| **📓 Journal & Scanning** | **🗺️ Map** |
| Scan with E to record discoveries | Full map for orientation |
| **💰 Shop & Upgrades** | **📊 Inventory System** |
| Sell your haul and buy gear at the boat *(1–5)* | Track everything you've collected |
| **💾 Auto-save** | **📱 Mobile Support** |
| Money, upgrades, and journal saved in your browser | Touch controls with landscape layout |
| **🖥️ Desktop Support** | **🚫 Zero Dependencies** |
| Full keyboard + mouse controls | No install, no server, no assets to download |

</div>

---

## 🏗️ Architecture

### System Overview

```mermaid
flowchart TB
    subgraph FILE["📄 index.html — The Entire Game"]
        direction TB

        subgraph RENDER["🎨 Rendering"]
            Scene["Three.js 3D Scene<br/>underwater world"]
            Water["Water & Fog"]
            Lighting["Dynamic Lighting<br/>flashlight · ambient"]
        end

        subgraph GAME["⚙️ Game Logic"]
            Player["Player Controller<br/>swim · ascend · descend<br/>look · sprint"]
            Harpoon["Harpoon System<br/>Q"]
            Scan["Scan System<br/>E"]
            Journal["Journal<br/>discoveries"]
            Inventory["Inventory<br/>collected items"]
        end

        subgraph WORLD["🌍 World"]
            Boat["Boat<br/>shop · surface"]
            Abyss["The Abyss<br/>explorable depth"]
            Creatures["Creatures & Objects<br/>collectable · scannable"]
        end

        subgraph UI["🖥️ UI"]
            HUD["HUD<br/>oxygen · depth · money"]
            Menus["Menus<br/>inventory · journal · map · pause"]
            Shop["Shop UI<br/>at the boat"]
        end

        subgraph INPUT["🎮 Input"]
            Keyboard["Keyboard + Mouse"]
            Touch["Touch Controls<br/>stick · drag · buttons"]
        end

        subgraph PERSIST["💾 Persistence"]
            LS[("LocalStorage<br/>money · upgrades · journal")]
        end
    end

    INPUT --> GAME
    GAME --> RENDER
    RENDER --> WORLD
    GAME --> UI
    GAME --> PERSIST

    style FILE fill:#1e293b,color:#fff
    style RENDER fill:#0EA5E9,color:#fff
    style GAME fill:#8B5CF6,color:#fff
    style WORLD fill:#22C55E,color:#fff
    style UI fill:#FFB454,color:#000
    style INPUT fill:#FF6B6B,color:#fff
    style PERSIST fill:#316192,color:#fff
```

### Design Principles

<div align="center">

| Principle | Implementation |
|-----------|---------------|
| **📄 One file, zero dependencies** | The whole game is `index.html` — **no install, no server, no external assets** |
| **🖥️ Desktop and mobile parity** | **Full keyboard + mouse** on desktop, **stick + buttons** on mobile — **every action has both** |
| **🔦 Darkness is the mechanic** | The **flashlight** isn't cosmetic — **it's how you explore the abyss** |
| **📓 Discovery rewards** | **Scanning records discoveries in the journal** — **exploration has lasting value** |
| **💰 Economic loop** | **Collect → Surface → Sell → Upgrade → Dive deeper** — **progress compounds** |
| **💾 Auto-save without a backend** | **Money, upgrades, and journal** saved in `localStorage` |
| **📱 Landscape-first on mobile** | **Rotate to landscape** — **the game is designed for it** |

</div>

---

## 💾 Progress & Saving

> **Progress (money, upgrades, journal) auto-saves in your browser.**

### 🔄 Starting Fresh

**Clear this site's data** in your browser's settings.

> 💡 **The game detects missing or corrupted save data and starts fresh without crashing.**

---

## 🗺️ Roadmap

### ✅ Current

- [x] Single-file, dependency-free browser game
- [x] Three.js 3D underwater world
- [x] Dive from the boat into the abyss
- [x] Free exploration with WASD + mouse look *(desktop)* or stick + drag *(mobile)*
- [x] Ascend and descend controls on both desktop and touch
- [x] Sprint / fast movement toggle
- [x] Flashlight toggled with `F`
- [x] Harpoon action with `Q`
- [x] Interact / Collect / Scan / Sell with `E`
- [x] Scan discoveries recorded in the journal
- [x] Full inventory system
- [x] Full journal system
- [x] Map accessible with `M`
- [x] Pause with `Esc`
- [x] Shop at the boat with quick keys `1–5`
- [x] Money, upgrades, and journal auto-saved in `localStorage`
- [x] Works offline
- [x] Desktop support with full keyboard and mouse controls
- [x] Mobile support with touch controls
- [x] Landscape orientation on mobile
- [x] Deployable to any static host

### 🔜 Future Ideas

- [ ] **Additional abyss zones** — deeper, darker, more dangerous
- [ ] **More creature types** — beyond the current collectables
- [ ] **More harpoon targets** and mechanics
- [ ] **Oxygen system** — adding survival pressure
- [ ] **More upgrades** beyond the current shop
- [ ] **Achievements** — for milestones and rare discoveries
- [ ] **Ambient music** — synthesized with Web Audio
- [ ] **Underwater sound effects** — bubbles, harpoon, scanning
- [ ] **Local leaderboards** — deepest dive, highest haul
- [ ] **PWA support** — install and play offline
- [ ] **Save export/import** — for cross-device portability

---

## 🤝 Contributing

Contributions are welcome. Please:

1. Fork the repository
2. **Keep it single-file** — no external build step, no bundler
3. **Keep it dependency-free** — no assets to download
4. **Preserve both input paths** — desktop and mobile must both work
5. **Keep the flashlight meaningful** — darkness is the mechanic
6. **Keep scanning valuable** — journal records must persist
7. **Preserve LocalStorage compatibility** without a migration path
8. **Keep it working offline**
9. **Test in landscape on mobile** before submitting
10. Submit a Pull Request

### Guidelines

- **Never require a backend** — the game must work from `file://`
- **Never add a required external dependency** beyond Three.js
- **Never break the auto-save** — money, upgrades, and journal must persist
- **Never remove the mobile controls** — both platforms matter
- **Never present a stub as a feature**

---

## 📜 License

MIT — see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments

- **Three.js** — for making an underwater world this immersive
- **Every deep-sea explorer who ever looked down and wondered how far it goes** — this one's for you

---

<div align="center">

### 🌊 DIVE. EXPLORE. COLLECT. SURVIVE.

**A browser-based 3D underwater exploration game.**

**Zero install. Zero dependencies. Works offline.**

<br>

> 💾 **Progress auto-saves in your browser — clear site data to start fresh.**

<br>

⭐ If DEEP BLUE took you to the abyss and back, consider giving it a star.

<br>

[⬆ Back to Top](#-deep-blue-abyss-explorer)

</div>
