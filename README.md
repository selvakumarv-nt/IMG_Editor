# 🎨 PixelCraft – Image Editing Studio

[![Technology](https://img.shields.io/badge/Stack-HTML5%20%7C%20CSS3%20%7C%20Vanilla%20JS-blue.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Dependencies](https://img.shields.io/badge/Dependencies-Zero%20(None)-brightgreen.svg)](#mandatory-technology-stack)
[![Offline Capable](https://img.shields.io/badge/Offline-100%25%20Functional-success.svg)](#privacy--offline-first)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](#license)

**PixelCraft** is a lightweight, desktop-class photo and graphic editing application that runs entirely inside your web browser. Built strictly with native web standards—**HTML5, CSS3, Vanilla JavaScript, HTML5 Canvas, File API, Blob API, and ImageData API**—it requires no frameworks, no build tools, no servers, and no external CDNs.

---

## 🌟 Highlights & Philosophy

- **100% Client-Side:** All image processing algorithms run locally on the client's CPU via direct pixel-buffer manipulation (`ImageData`).
- **Zero Dependencies:** No React, Vue, jQuery, Tailwind, Bootstrap, FontAwesome, or external CDNs.
- **Privacy & Offline First:** Your images are never transmitted over the internet or uploaded to any server. Open the HTML file anywhere—even with no internet connection.
- **Desktop-Inspired UI:** Features standard workspace layouts including multi-document tabs, toolbars, options bars, layer stacks, adjustment sliders, and history states.

---

## 🚀 Features

### 1. File Management & Multi-Document Tabs
- **Drag & Drop:** Drop any image onto the workspace to open it instantly.
- **File Dialog:** Open files via `File > Open Image...` or upload multiple images at once.
- **Multiple Tabs:** Edit multiple images concurrently using the tab bar.
- **Supported Formats:** PNG, JPEG/JPG, WebP, BMP, and SVG.
- **Non-Destructive Originals:** The pristine version of each uploaded image is cached in memory for comparison and resetting.

### 2. Workspace & Navigation
- **Infinite Canvas & Viewport:** Smooth panning and zooming from **10% up to 500%**.
- **Mouse & Trackpad Support:** Smooth scroll-wheel zoom centered on cursor.
- **Pan Tool (`H` or `Spacebar`):** Click and drag to pan across large canvases.
- **Checkerboard Background:** Clear visual representation of transparency and alpha channels.
- **Dark & Light Mode:** Toggle themes anytime via the `File` menu.

### 3. Professional Adjustment Engine (ImageData API)
PixelCraft processes pixel buffers directly with mathematically accurate algorithms:
- **Lighting:** Brightness, Contrast, Exposure (EV stops), Highlights, Shadows, and Gamma correction ($γ$ curve).
- **Color Balance:** Saturation, Vibrance, Color Temperature (Warm/Cool), Tint, Hue Rotation ($0^\circ–360^\circ$), and individual RGB channel mixers.
- **Detail & Quality:** 
  - **Sharpness:** Authentic $3 \times 3$ Laplacian kernel convolution matrix.
  - **Effects:** Vignette radial gradient, synthetic film grain generator, pixelation downsampling, posterization quantization, and color inversion.
- **Bake Adjustments:** Commit non-destructive real-time adjustments directly into the active layer pixel data.

### 4. 15 Algorithmic Filter Presets
One-click presets with an adjustable **Intensity Slider (0–100%)** and live canvas-rendered thumbnails:
1. **Original**
2. **Grayscale**
3. **Sepia**
4. **Vintage**
5. **Black & White**
6. **Warm**
7. **Cool**
8. **Cinematic (Teal & Orange)**
9. **Dramatic**
10. **Faded**
11. **High Contrast**
12. **Soft Portrait**
13. **Retro**
14. **Monochrome**
15. **Vivid**

### 5. Multi-Layer Compositing System
- **Stack Operations:** Add, duplicate, reorder (Move Up / Down), and delete layers.
- **Layer Controls:** Toggle visibility (👁), layer locking (🔒), layer opacity ($0–100\%$), and inline renaming.
- **Canvas Blend Modes:** Supports `normal`, `multiply`, `screen`, `overlay`, `darken`, `lighten`, `color-dodge`, and `difference`.

### 6. Creative & Drawing Tools
- **Paint Brush (`B`):** Freehand drawing with adjustable size, opacity, hardness, and color picker.
- **Eraser (`E`):** Erases drawn elements to alpha transparency using `destination-out` compositing.
- **Shape Generator (`U`):** Draw Rectangles, Ellipses/Circles, Lines, and directional Arrows with configurable stroke width and fill modes.
- **Typography Engine (`T`):** Add editable text overlays with custom font family, size, bold/italic styles, and alignment.
- **Watermark Tool:** Apply custom text watermarks with opacity adjustments and positioning presets (Center, Corners, or a repeating $30^\circ$ diagonal pattern).

### 7. Canvas & Geometry Transformations
- **Crop Tool (`C`):** Freeform or fixed aspect ratios (`1:1`, `16:9`, `4:3`, `9:16`) with interactive boundary handles and live guides.
- **Rotation:** Rotate $90^\circ$ CW, $90^\circ$ CCW, or $180^\circ$.
- **Flipping:** Flip horizontally or vertically.
- **Resize Image:** Change image dimensions with high-quality bicubic canvas interpolation and aspect-ratio locking.
- **Canvas Size:** Extend canvas borders with configurable background color fills.

### 8. Comparison & History System
- **Before / After Split Slider (`Tab`):** Compare your edits side-by-side against the untouched original image using an interactive divider.
- **History Timeline:** Complete action stack with non-destructive state restoration.
- **Undo / Redo:** Full support for `Ctrl + Z` and `Ctrl + Y`.

### 9. Export Options
- **Formats:** Export to **PNG** (lossless alpha), **JPEG** (custom compression), or **WebP** (modern high-efficiency format).
- **Quality Slider:** Fine-tune file size versus visual fidelity before downloading.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `V` | Select / Move Tool |
| `C` | Crop Tool |
| `B` | Paint Brush Tool |
| `E` | Eraser Tool |
| `T` | Text Tool |
| `U` | Shape Tool |
| `H` / `Space + Drag` | Pan / Hand Tool |
| `Tab` | Toggle Interactive Split Comparison |
| `Ctrl + Z` | Undo last operation |
| `Ctrl + Y` | Redo operation |
| `Ctrl + S` | Open Export / Save Dialog |
| `Ctrl + 0` | Fit image to screen |
| `Ctrl + 1` | Zoom to actual 100% scale |
| `Ctrl + +` / `Ctrl + -` | Zoom in / Zoom out |

*(On macOS, substitute `Ctrl` with `Cmd`.)*

---

## 🛠️ Project Structure & Architecture

Because PixelCraft requires zero compilation or external assets, the entire application can live in a clean single-file format or modular directory structure:
pixelcraft/
│
├── index.html # UI markup, SVGs, style themes, and processing engine
└── README.md # Documentation
Code
### Core Architecture Components
Code
┌──────────────────────────────────────┐
               │           User Interaction           │
               │  (Mouse, Keyboard, Sliders, Tools)   │
               └──────────────────┬───────────────────┘
                                  │
                                  ▼
               ┌──────────────────────────────────────┐
               │           Document Manager           │
               │  (Tabs, State, Canvas Dimensions)    │
               └──────────────────┬───────────────────┘
                                  │
    ┌─────────────────────────────┼─────────────────────────────┐
    ▼                             ▼                             ▼
┌───────────────┐ ┌───────────────┐ ┌───────────────┐
│ Layer System │ │ History Stack │ │ Pixel Engine │
│ Compositing & │ │ State Caching │ │ (ImageData │
│ Blend Modes │ │ & Snapshots │ │ Convolution) │
└───────┬───────┘ └───────┬───────┘ └───────┬───────┘
│ │ │
└─────────────────────────────┼─────────────────────────────┘
│
▼
┌──────────────────────────────────────┐
│ Canvas Viewport Engine │
│ (Pan, Zoom, Overlays, Displays) │
└──────────────────────────────────────┘
Code
---

## 🚦 Getting Started

### Option 1: Direct Browser Launch (No Setup)
1. Download or clone this repository.
2. Double-click `index.html` (or right-click → **Open With** → Google Chrome, Firefox, Microsoft Edge, Safari, or Brave).
3. Start editing immediately!

🔒 Privacy & Offline First
Zero Network Calls: PixelCraft makes zero network requests during operation.
No Analytics / Telemetry: No tracking pixels, analytics scripts, or cookies are included.
Air-Gapped Ready: Can be safely loaded and used in classified or air-gapped secure environments.
