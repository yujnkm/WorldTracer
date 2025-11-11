# World Tracer (v1.4)

!(image-placeholder-1.png)

[cite_start]This tool is a rapid 3D environment generator that transforms 2D robot mapping data into 3D digital twins[cite: 3]. [cite_start]It uses the bitmap (PNG) images from a robot's SLAM or LiDAR data as a "scaffold"[cite: 4]. [cite_start]A user can then simply trace the walls and objects on the 2D image, and the tool instantly converts these traces into a 3D model that can be exported for use in simulations[cite: 5].

### Core Features
* [cite_start]**Speed:** Generates complex 3D floor plans in minutes, not hours[cite: 13].
* [cite_start]**Ease of Use:** Bypasses complex 3D modeling software; if you can trace an image, you can use this tool[cite: 14].
* [cite_start]**Ideal for Reinforcement Learning:** The models are perfect, lightweight environments for training AI agents[cite: 15]. [cite_start]They provide the up-to-date "state" of the world needed for effective RL training[cite: 16].
* [cite_start]**Dynamic Updates:** Can create a new digital twin as frequently as a robot completes its route, allowing AI models to adapt to real-time environmental changes[cite: 17].
* [cite_start]**Server-Side Computation:** The entire process can be run on a server, meaning models can be generated without requiring powerful local computers[cite: 18].
* [cite_start]**Simulation-Ready:** Models are built to be exported and used immediately in physics simulations to train and validate AI/DNN navigation models[cite: 19].

### Primary Use Case: Reinforcement Learning

[cite_start]The tool's primary value is its speed and simplicity, providing a dynamic training ground for Reinforcement Learning (RL)[cite: 7].

[cite_start]Instead of training on a single, outdated blueprint, AI agents can train in an "almost live" digital twin that represents the factory's current layout, which can be updated every 5-10 minutes[cite: 8]. [cite_start]This is critical for optimizing autonomous robot fleets (like Omron AMRs)[cite: 9]. [cite_start]Using RL, AI agents can safely explore and learn optimal navigation policies (speed, cornering, routing) within this constantly-updated simulation[cite: 10]. [cite_start]The goal is to discover behaviors that maximize efficiency while minimizing penalties like collisions or traffic congestion[cite: 11].

### Get Started

This repository provides the Unity project files and server-side code to run World Tracer. Follow the setup instructions below to begin.

---

## System Requirements

### Unity Client
* [cite_start]**Unity Version:** Unity 2020.3.12 [cite: 27]

### Server (Optional)
* [cite_start]**NodeJs** [cite: 258]
* [cite_start]**Node Package Manager (npm)** [cite: 259]
* [cite_start]**Assimp CLI** (Open Asset Importer library) [cite: 260]

---

## Setup Instructions

### 1. Unity Client Installation

1.  [cite_start]Clone the Repo[cite: 26].
2.  [cite_start]Download and install **Unity 2020.3.12** from the Unity Download Archive[cite: 27].
3.  [cite_start]Open the `/TheFactory/` directory in Unity[cite: 29]. [cite_start]Opening it for the first time will take time as Unity generates new files[cite: 29].
4.  [cite_start]In the *Project* window, navigate to `Assets/Sketching/Scenes/ExampleDrawingScene.unit`[cite: 33].
5.  [cite_start]Press the **Play** button to run the tool in the Unity Engine[cite: 30, 32].

### 2. Import SLAM Map

1.  [cite_start]Press the "Import SLAM Map" button[cite: 76].
2.  [cite_start]Enter the file path to your `.png` map image (e.g., `D:/SlamMap_03.png`)[cite: 78, 79, 86]. [cite_start]The text will turn green when the path is valid[cite: 87].
3.  [cite_start]Enter the **Scale (pixels per meter)** (e.g., 60)[cite: 80, 89].
    * [cite_start]*Tip: If your floor plan image appears to be too small, try lowering the Scale value*[cite: 90].
4.  [cite_start]Enter the **Origin (in pixels)**, which should match your image's dimensions (e.g., Width 400, Height 400)[cite: 81, 88, 92].
5.  [cite_start]Press **Import**[cite: 84, 91]. [cite_start]You may need to click and drag (pan) or use the mouse scroll (zoom) to center your floor plan[cite: 91].
    ![Import SLAM Map dialog](image-placeholder-import.png)

### 3. Tracing the Layout

1.  [cite_start]Use the **Draw View** button to return to the top-down birdseye view for tracing[cite: 138, 156].
2.  [cite_start]Use the **Extrude View** button to investigate your extruded 3D walls and objects[cite: 138]. [cite_start]You can toggle between views while you work[cite: 142].
3.  **To Trace Walls:**
    * [cite_start]Select the **line tool** from the center toolbar[cite: 150].
    * [cite_start]From the dropdown menu on the left, select **"Wall"** and start tracing[cite: 151].
    * [cite_start]Select the button with the **"wall logo"** to apply the 3D wall[cite: 154]. [cite_start]The view will automatically shift to "Extrude View"[cite: 155].
4.  **To Trace Objects:**
    * [cite_start]Select the **line tool**[cite: 162].
    * [cite_start]From the dropdown menu, select **"Object"** and start tracing[cite: 163].
    * [cite_start]Select the "wall logo" button to apply the 3D object[cite: 165].
    * [cite_start]**Note:** "Object" creates a sealed 3D object and requires the lines to be looped, not a standalone line[cite: 170].
    ![Tracing a wall in Draw View](image-placeholder-trace-wall.png)
    ![Extruded 3D wall view](image-placeholder-extrude-wall.png)

### 4. Adjustments and Exporting

1.  **Fine Adjustments:**
    * [cite_start]Fine adjustments can be made even after a wall/object is built[cite: 197].
    * [cite_start]Click the **correction tool** (red cursor icon) in the center tool panel[cite: 197].
    * [cite_start]Grab a joint (it will highlight yellow when selected) and drag it to readjust the position[cite: 198, 199].
2.  **Exporting:**
    * [cite_start]Click the **import/export logo** (top-left toolbar)[cite: 201].
    * [cite_start]The **"Save"** option can be used to save the vertex mesh[cite: 219].
    * [cite_start]The **"Export"** option can be used to export and save the model as an `.obj` or `.fbx` file[cite: 238].
    ![Export Menu](image-placeholder-export.png)

### 5. Server Installation (Optional)

[cite_start]Instructions for installing and running the server[cite: 251].

1.  [cite_start]**Install Packages**[cite: 256]:
    * **DEBIAN:**
        ```bash
        sudo apt install nodejs npm
        sudo apt install assimp-utils
        ```
        [cite_start][cite: 262, 263]
    * **MACOS:**
        ```bash
        brew install nodejs
        brew install npm
        brew install assimp
        ```
        [cite_start][cite: 265, 266, 267]
    * **WINDOWS:**
        * [cite_start]Install Windows Subsystem for Linux (WSL)[cite: 269].
        * [cite_start]Run the server on Ubuntu, following the "DEBIAN" instructions[cite: 270].
2.  **Run the Server:**
    * [cite_start]The first time you run, you must enter `npm install` into the command line[cite: 276].
    * [cite_start]Run `node index.js` from the `/SampleServer/` directory[cite: 281]. [cite_start]You may need `sudo` for some Linux distributions[cite: 281].

---

## Notes

* [cite_start]**Flat-Floor Assumption:** The tool is currently optimized for environments with flat floors[cite: 21]. [cite_start]It does not automatically capture or identify vertical changes in the layout, such as elevation differences, ramps, inclines, or floor tilt, as it is working from a 2D-plane SLAM projection[cite: 22].
* [cite_start]**VPN Required:** Access to the GitLab and server demo links in the original manual requires a corporate VPN connection[cite: 244].

---

## Authorship and Citation Policy
[cite_start]This repository may contain 3D models constructed with significant care and effort[cite: 357]. [cite_start]If you use any of the models in your research, academic publications, class projects, or syllabi, we kindly request that you please cite this work[cite: 358].

### Citation Requirement
[cite_start]Please use the following format for citation[cite: 359]:

> Kim, Y. (2021). UCSB\_3D Campus (Version 1.0.1) \[Computer software]. available
> at: https://github.com/yujnkm/UCSB_3D (accessed 19 May
> [cite_start]2022). https://doi.org/10.5281/zenodo.6565136 [cite: 360, 361, 362]

### BibTeX Entry:

```bibtex
@software{Kim_2021_UCSB3D,
  author = {Kim, Y.},
  title = {{UCSB\_3D Campus}},
  version = {1.0.1},
  publisher = {Zenodo},
  year = {2021},
  doi = {10.5281/zenodo.6565136},
  url = {[https://doi.org/10.5281/zenodo.6565136](https://doi.org/10.5281/zenodo.6565136)}
}
