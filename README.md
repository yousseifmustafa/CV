# Project Overview

Welcome to Task 1 of our Computer Vision (CV) course! In this project, our team will be performing image annotation on a 'Rock, Paper, Scissors' dataset. Accurate data labeling is a crucial step in building robust computer vision models, and your contribution here will directly impact our machine learning pipeline.

This guide will walk you through the necessary tools, environment setup, and the exact steps needed to complete your assigned annotations accurately.

---

## Prerequisites & Environment Setup

Before starting the annotation process, you need to set up the appropriate Python environment. We will use `conda` to create an isolated environment with all the necessary dependencies.

1. **Create the Conda Environment:**
   Run the following command to create a new environment named `cv` with Python 3.10:
   ```bash
   conda create -n cv python=3.10
   ```
2. **Activate the Environment:**
   ```bash
   conda activate cv
   ```
3. **Install Dependencies:**
   Once activated, install the required packages (`pyqt5` and `lxml`) used by the labelImg tool:
   ```bash
   pip install pyqt5 lxml
   ```

> [!CAUTION]
> **Fixing the `pyrcc5` Command Issue**
> When building `labelImg`, you need to run the `pyrcc5` command. To avoid typos (which are very common here), simply copy and paste the exact command below while inside your `labelImg-master` directory:
> ```bash
> pyrcc5 -o libs/resources.py resources.qrc
> ```
> Ensure you run this *after* activating your `cv` environment!

---

## Folder Structure

Our project relies on a specific directory structure. All labeling work must conform to this setup to avoid issues later in the training pipeline. Please ensure your local setup looks exactly like this under your `Task_1` folder:

```text
Task_1/
├── images/     # (Where the photos to be labeled are located)
├── labels/     # (Where your output .txt annotation files should go)
├── data.yaml   # (The configuration file for training)
└── classes.txt # (Contains: Rock, Paper, Scissors)
```

### Dataset Download

You can download a suitable Rock-Paper-Scissors dataset from Roboflow over here: [Rock-Paper-Scissors Dataset](https://universe.roboflow.com/search?q=rock-paper-scissors).

1. Choose a dataset and download it as a ZIP file.
2. Select 20 images to contribute towards the task.
3. Place these 20 images inside your `Task_1/images/` directory.

---

## Step-by-Step Annotation Guide using labelImg

We will be using `labelImg` to draw bounding boxes around the subjects in our images. Follow these exact steps:

1. **Launch labelImg:** Start the `labelImg` tool from your terminal within the `cv` conda environment.
2. **Open the Images Directory:**
   - In labelImg, click on **Open Dir** on the left menu (or use the shortcut).
   - Navigate to and select your `Task_1/images/` folder.
3. **Set the Save Directory for Labels:**
   - Click on **Change Save Dir** on the left menu.
   - Navigate to and select your `Task_1/labels/` folder. This ensures all your annotations are saved in the correct spot.
4. **Use Predefined Classes:**
   Make sure you are using the predefined `classes.txt` file which enforces the following standard classes for consistency across the entire team:
   - `0`: Rock
   - `1`: Paper
   - `2`: Scissors

> [!IMPORTANT]
> **Crucial Step: Switch Format to YOLO**
> By default, labelImg might save annotations in PascalVOC format (XML files). **You MUST switch this to YOLO format (.txt files).**
> Find the save format button on the left panel (it usually says "PascalVOC"). Click it until it changes to **YOLO**.

### Keyboard Shortcuts

Using shortcuts will make your annotation process much faster:

- **`W`**: Create a bounding box (RectBox)
- **`D`**: Go to the next image
- **`A`**: Go to the previous image
- **`Ctrl + S`**: Save the current annotation

---

## Final Submission Rules

To ensure a smooth handoff and integration of everyone's data, strictly follow these final rules:

1. **Complete Your Quota:** Each team member _must_ finish annotating all of their assigned images.
2. **Naming Consistency:** All generated label files in the `labels` folder must have the exact same base name as their corresponding image file in the `images` folder (e.g., if you have `rock_01.jpg`, you must have `rock_01.txt`).
3. **YOLO Format Only:** Double-check that your output files are plain text files (`.txt`) and not `.xml`.

Thank you for your hard work—consistent and precise labeling makes all the difference! If you run into any issues, reach out to the team for help.
