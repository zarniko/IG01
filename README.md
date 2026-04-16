# IG01 — Instrument Grid 01

A 16×16 step sequencer for the browser. No install, no build step — open `index.html` and play.

Built as a single self-contained HTML file using the Web Audio API.

---

## Features

**Sequencer**
- 16×16 grid — rows are pitches, columns are time steps
- 8 independent pattern pages, switchable mid-playback
- Copy / paste patterns between pages
- Per-row mute with animated indicator
- BPM range 40–240

**Sound**
- 4 oscillator types: sine, triangle, square, sawtooth
- 35 scales including pentatonic, modal, blues, raga, world, and interval sets
- Per-note: volume, decay, attack, detune, filter cutoff + resonance, distortion, delay send, reverb send
- Global FX chain: high-pass filter, low-pass filter, convolution reverb, stereo delay with feedback, tremolo LFO

**Random generator**
- Generates musically structured patterns using Euclidean rhythms (Bjorklund algorithm), polyrhythm, and anchor-scatter strategies
- Randomizes BPM, scale, wave palette, and all FX values within ambient/downtempo ranges
- Register-aware: bass rows get long sine tails, upper rows get sparse shorter notes

**Session**
- Save full session to a `.json` file (all 8 pages + all settings)
- Load session from file
- Share via compressed URL hash — the entire session fits in a link

**Interface**
- CRT aesthetic: scanlines, vignette, film grain, monochrome glow
- Topo viz: audio-reactive marching-squares terrain animation
- Oscilloscope in FX panel
- 8-color accent palette
- Responsive layout — works on mobile

---

## Usage

Open `index.html` in any modern browser. No server required.

### Keyboard shortcuts

| Key | Action |
|-----|--------|
| `space` | play / stop |
| `R` | generate random pattern |
| `C` | clear current page |
| `H` | toggle help overlay |
| `1` – `8` | switch page |
| `↑` | copy current page |
| `↓` | paste to current page |
| `shift` (hold) | open per-note FX panel |

### Grid interaction

| Action | Result |
|--------|--------|
| Click empty cell | place note |
| Drag on empty cells | paint notes |
| Click active note | select (inspect / edit) |
| Click selected note | erase |
| Drag on active notes | erase |

### Mobile

Tap to place, tap again to select, long-press to erase, drag to paint.

---

## Requirements

A modern browser with Web Audio API support. Chrome, Firefox, Safari, Edge — all current versions work. No internet connection required after first load (Google Fonts will fall back to system monospace).

---

## Tech

Single HTML file. ~2500 lines. Zero dependencies beyond Web Audio API and a Google Fonts import.

- Audio: Web Audio API (oscillators, biquad filters, convolution reverb, delay, waveshaper distortion)
- Visuals: Canvas 2D (topo viz via marching squares, film grain, oscilloscope)
- Session compression: native `CompressionStream` API (deflate-raw)
- Font: Share Tech Mono

---

*zko.io*

