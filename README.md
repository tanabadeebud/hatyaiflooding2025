# Hat Yai Flood 2025: Radar Rainfall Analysis & Early Warning System

<p align="left">
  <img src="Radar4flood_Icon_PNG.png" alt="Radar4Flood Logo" width="120" height="120">
</p>

An advanced, interactive web dashboard designed for hydrodynamic tracking, data aggregation, and spatial analysis of the extreme precipitation event affecting Hat Yai, Thailand, in November 2025. 

This platform acts as an open-source visual interface leveraging calibrated radar matrices alongside ground-truth measurements to optimize multi-hazard early warning pipelines for flash floods and urban inundation.

---

## 🗺️ Key Features

*   **Synchronized 3x3 Daily Map Grid**: A high-performance, locked-extent multi-map array built on Leaflet.js that displays pixel-perfect daily accumulated radar rainfall across the basin profile simultaneously.
*   **Meteorological Accumulation Pipeline**: Custom client-side data handling that processes raw hourly radar JSON matrix outputs over true meteorological windows (08:00 to 07:00 next-day).
*   **Dual-Language Infrastructure**: Full native toggle support for **English (EN)** and **Thai (TH)** across all analytical contexts, labels, and map tools.
*   **Spatial Boundary Overlays**: Dynamic GeoJSON mapping layers providing localized administrative and watershed/basin context across synchronized views.

---

## 🛠️ Architecture & Pipeline

The system is optimized for lightweight, client-side execution, bypassing heavy geospatial servers by rendering raw multidimensional matrix payloads directly onto an HTML5 Canvas overlay.

### 1. Radar Processing Window
Rather than using standard calendar days, the dashboard runs automated pipeline checks to sum data over hydrologically relevant windows:
*   **Primary Track**: Accumulated from Day $(N-1)$ at `08:00:00` through Day $N$ at `07:00:00`.
*   **Fallback Mode**: Automated recovery script that falls back to localized current-day window matrices (`07:00:00` to `23:00:00`) if edge-file source data is delayed.

### 2. Interaction Safety
To maintain precise structural alignment across temporal matrix comparisons, map instances are programmatically locked:
*   Scroll-wheel zoom, panning/dragging, double-click zoom, and touch gestures are disabled.
*   Spatial cross-map coordinate syncing runs on an efficient `mousemove` handler to isolate data queries via non-intrusive synchronized hover popups.

---

## 📂 Repository Structure

```text
├── data/
│   └── basin_boundary.geojson    # Watershed geometry vectors
├── data_json/
│   └── data_YYYYMMDDHH0000.json  # Raw hourly radar matrix arrays
├── index.html                    # Project Homepage
├── daily_radar.html              # 3x3 Daily Accumulated Grid Map
├── rainfall_stations.html        # Animated Radar Playback View
├── gauge_stations.html           # Ground-Truth Rain Gauge Data
├── water_levels.html             # Hydraulic River Stage Data
├── district_rainfall.html        # Zonal Accumulated Rainfall Tables
├── flood_mapping.html            # Remotely Sensed/Inundation Layers
└── Radar4flood_Icon_PNG.png      # Official Project Logo
