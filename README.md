

# 🏥 Medicare.ai — Multi-Agent Medical Assistant using LangGraph 

**Medicare.ai** is a multi-agent medical assistant system built using **LangGraph**, enabling natural language interaction between patients and AI agents for tasks like fetching doctor availability and booking appointments. The system uses **Groq**-accelerated **LLaMA-3-8b** models for high-speed inference and response generation, providing a scalable, intelligent interface for medical query handling and scheduling.

---

## 🚀 Key Features

* 🧠 **LLM-Powered Agents**: Uses Groq + LLaMA-3-8b for high-speed, accurate intent recognition and dialogue.
* 👨‍⚕️ **Doctor Matching**: Finds relevant doctors based on patient symptoms.
* 📅 **Availability Management**: Checks and displays doctor availability.
* 📝 **Appointment Booking**: Automatically updates the database to book slots.
* 🧩 **Modular Agent System**: Built using LangGraph with clear separation of logic.
* 💻 **Streamlit UI**: Simple web interface for patients to interact with agents.

---

## 🧱 Architecture Overview

```
User Input (Streamlit UI)
        ↓
    LangGraph Router
        ↓
  ┌────────────┬────────────┐
  │            │            │
Doctor Agent  Booking Agent  Prompt Agent
  │            │            │
  └────┬───────┴──────┬─────┘
       ↓              ↓
  data_models       utils/llms
       ↓              ↓
    CSV DB       Groq + LLaMA
```

---

## 🧰 Tech Stack

| Component        | Tool/Framework                          |
| ---------------- | --------------------------------------- |
| LLM Backend      | [Groq](https://groq.com/) + LLaMA       |
| Agent Framework  | [LangGraph](https://www.langgraph.dev/) |
| UI               | [Streamlit](https://streamlit.io)       |
| Programming Lang | Python                                  |
| Data Storage     | CSV-based (local)                       |

---

## 📁 Project Structure

```
medicare.ai/
│
├── data/                          # Raw data files
│   └── doctor_availability.csv
│
├── notebook/                      # Exploratory notebooks
│   └── availability.csv
│
├── data_models/                   # Pydantic models and DB logic
│   ├── __init__.py
│   └── models.py
│
├── prompt_library/               # Prompt templates and logic
│   ├── __init__.py
│   └── prompt.py
│
├── toolkit/                      # Helper functions and tools
│   ├── __init__.py
│   └── toolkits.py
│
├── utils/
│   ├── __init__.py
│   └── llms.py                   # Groq + LLaMA LLM integration
│
├── agent.py                      # Agent definitions using LangGraph
├── main.py                       # Main entrypoint to build the graph
├── streamlit_ui.py               # Streamlit front-end
├── setup.py                      # Package setup
├── requirements.txt              # Dependencies
├── LICENSE
└── README.md                     # You are here!
```

---

## 🧠 How It Works

1. **User Input**
   The patient inputs symptoms via a Streamlit UI.

2. **LLM Parsing (Groq + LLaMA)**
   The input is sent to a Groq-hosted LLaMA model to parse intent (e.g., check availability, book appointment).

3. **Agent Routing via LangGraph**

   * If it's an **information query**, Doctor Agent fetches the relevant data.
   * If it's a **booking intent**, Booking Agent writes to the CSV backend.
   * Prompts and clarifications are handled via Prompt Agent.

4. **Response Generation**
   The system formats and returns a natural response back to the patient.

---

## ⚙️ Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/riddhiman-ghatak/medicare.ai.git
cd medicare.ai
```

### 2. Install Requirements

```bash
pip install -r requirements.txt
```

### 3. Run Streamlit UI

```bash
streamlit run streamlit_ui.py
```

Make sure your Groq API key and environment settings are correctly configured (if using `.env`, update accordingly).

---

## 🧪 Sample Use Cases

* *Patient*: “I have chest pain, who should I consult?”

* *System*: “Dr. A from Cardiology is available on Tuesday and Friday. Want me to book a slot?”

* *Patient*: “Book a neurologist for Saturday.”

* *System*: “Booked an appointment with Dr. B on Saturday at 11:30 AM.”

---

## ✅ To-Do

* [ ] Integrate RAG-based document retrieval
* [ ] Add vector DB for richer symptom-doctor mapping
* [ ] Include patient history tracking
* [ ] Cloud deployment (GCP / AWS)



