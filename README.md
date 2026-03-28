# Fitness-assistant

An offline AI-powered fitness assistant built with Python and Llama 3.2. Enter your stats and goals to get a personalised weekly workout plan displayed as terminal tables and exported to Excel. Then chat with a local AI coach about exercises, nutrition, and recovery — no internet, no API, completely free.

Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Requirements](#system-requirements)
- [Setup Instructions](#setup-instructions)
- [How to Run](#how-to-run)
- [How It Works](#how-it-works)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)

---------------------------------------------------------------------------------------------------------------------------

Overview

This project generates a fully personalised weekly workout plan based on user inputs such as height, weight, age, fitness experience, exercise style preference, and weekly availability. It uses a locally running large language model (Llama 3.2) via Ollama — meaning no data is sent to any external server and no internet connection is required after the initial setup.

After the plan is generated, users can chat with an AI fitness coach that has full context of their profile and plan, answering questions about exercise form, nutrition, recovery, and plan modifications in real time.

---------------------------------------------------------------------------------------------------------------------------

Features

- Personalised weekly workout plan based on user profile
- Supports calisthenics, weighted gym training, or mixed styles
- BMI calculation and coaching notes using rule-based logic
- Plan displayed as formatted, colour-coded tables in the terminal
- Plan exported as a professionally styled Excel (.xlsx) file with 4 sheets:
  - Profile summary
  - Warm-up and cool-down routines
  - Full weekly schedule
  - Personalised coaching tips
- Conversational AI chat with full memory of your plan and profile
- 100% offline after setup — no API keys, no subscriptions, no cloud

---------------------------------------------------------------------------------------------------------------------------

Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.8+ | Core programming language |
| Ollama | Runs the LLM locally on your machine |
| Llama 3.2 3B | Open-source large language model by Meta |
| Rich | Formatted tables and styled terminal output |
| OpenPyXL | Excel file generation and formatting |

---------------------------------------------------------------------------------------------------------------------------

System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| RAM | 8 GB | 16 GB |
| Disk space | 3 GB free | 5 GB free |
| OS | Windows 10 / macOS 12 / Ubuntu 20.04 | Latest version |
| Python | 3.8 | 3.10 or higher |

---------------------------------------------------------------------------------------------------------------------------

Setup Instructions

Follow these steps in order. Each step must be completed before moving to the next.

# Step 1 — Install Python

1. Go to https://python.org/downloads
2. Download Python 3.10 or higher
3. Run the installer
4. **Important:** During installation, check the box that says **"Add Python to PATH"**
5. Verify installation by opening CMD and running:



# Step 2 — Install Ollama

Ollama is the tool that runs the AI model locally on your machine.

1. Go to https://ollama.com
2. Click **Download** and install for your operating system
3. After installation, Ollama runs silently in the background (check the system tray on Windows)
4. Verify installation by opening CMD and running:

ollama --version

# Step 3 — Download the Llama Model

This is a one-time download of approximately 2 GB.

Open CMD and run:

ollama pull llama3.2:3b

Wait for the download to complete. You should see a progress bar. Once done, verify it downloaded correctly:

ollama list

You should see `llama3.2:3b` in the list.


# Step 4 — Clone the Repository


git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name

Or download the ZIP from GitHub and extract it.


# Step 5 — Install Python Dependencies

Inside the project folder, run:

pip install -r requirements.txt


This installs the following libraries:
- `ollama` — Python client to communicate with Ollama
- `rich` — for formatted terminal tables
- `openpyxl` — for generating Excel files

---------------------------------------------------------------------------------------------------------------------------

How to Run

1. Make sure the **Ollama app is open and running** (check system tray)
2. Open CMD and navigate to the project folder:

cd path\to\your-repo-name

3. Run the application:

python workout_recommender_chat.py


---------------------------------------------------------------------------------------------------------------------------

How It Works

```
User inputs (name, age, height, weight, experience, goal, etc.)
                          ↓
          Rule-based BMI calculation and analysis
                          ↓
        Structured prompt built from user profile
                          ↓
      Prompt sent to Llama 3.2 running locally via Ollama
                          ↓
         Model returns workout plan as JSON output
                          ↓
        ┌─────────────────┴──────────────────┐
        ↓                                    ↓
Terminal tables                        Excel file
(Rich library)                      (OpenPyXL library)
        └─────────────────┬──────────────────┘
                          ↓
           Conversational chat loop opens
        (full profile + plan in system prompt)
                          ↓
        User asks questions, model answers with
          full context of who the user is
```

---------------------------------------------------------------------------------------------------------------------------

Project Structure


Fitness assistant

├── workout_recommender_chat.py   # Main application file

├── requirements.txt              # Python dependencies

├── .gitignore                    # Files excluded from git

└── README.md                     # This file


When you run it, it will also generate:

(your name)_workout_plan.xlsx         # Your exported Excel plan

---------------------------------------------------------------------------------------------------------------------------

Troubleshooting

**`ollama` is not recognized as a command**
→ Restart CMD after installing Ollama. It needs a fresh terminal to detect the new PATH.

**`python` is not recognized as a command**
→ Reinstall Python and make sure to check "Add Python to PATH" during installation.

**`pip` is not recognized**
→ Run `python -m pip install -r requirements.txt` instead.

**Connection refused / Error connecting to Ollama**
→ Ollama is not running. Open the Ollama app from your Start Menu, then try again.

**Model not found**
→ Run `ollama pull llama3.2:3b` again and wait for it to fully complete.

**JSON parse error during plan generation**
→ The model occasionally formats output incorrectly. Simply run the script again — it resolves on the next attempt.

---------------------------------------------------------------------------------------------------------------------------

Notes for Evaluators

- No API key or internet connection is required to run this project after setup
- The AI model (Llama 3.2) runs entirely on the local machine
- All generated Excel files are saved in the same directory as the script
- The chat session maintains full conversation history for contextual responses
- Tested on Windows 11 with Python 3.11 and Ollama 0.3.x

