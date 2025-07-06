#  Medical Chatbot - Gale AI Advisor

An intelligent AI-powered chatbot that answers medical queries using **The Gale Encyclopedia of Medicine** as its core knowledge base. It leverages LangChain, vector embeddings, and HuggingFace LLMs to provide accurate, context-driven answers in real time.

---

##  Demo Screenshot

![Chatbot Demo](https://github.com/pranav6905/medical_chatbot/blob/main/Demo.png)

---

##  Key Features

✅ Uses **The Gale Encyclopedia of Medicine** as its data source  
✅ PDF content is chunked and embedded using **FAISS** and **MiniLM**  
✅ Integrates **HuggingFace LLM (Mistral-7B-Instruct-v0.3)** for intelligent response generation  
✅ Custom prompt template to keep answers strictly within the context

---

##  How It Works

### 1. **PDF Processing**

- Loads all PDFs from the `/data/` folder using `PyPDFLoader`
- Splits content into chunks using `RecursiveCharacterTextSplitter`
- Embeds chunks using `sentence-transformers/all-MiniLM-L6-v2`
- Saves vector index using `FAISS`

### 2. **Chat Pipeline**

- Uses a custom prompt to restrict answers only to known context
- Loads FAISS vector index and retrieves top `k=3` relevant chunks
- Sends user query + context to HuggingFace LLM (`mistralai/Mistral-7B-Instruct-v0.3`)
- Streams back a clean, reliable medical answer to the user

---

##  Project Structure
```bash
medical-chatbot/
├── data/                 # Contains Gale Encyclopedia PDF(s)
├── vectorstore/          # Stores FAISS index
├── creating_memory.py    # Loads PDF, creates chunks, builds FAISS DB
├── medibot.py            # Streamlit chatbot app
├── .env                  # Stores HuggingFace token
├── requirements.txt      # Python dependencies
└── README.md             # This file
```
##  Data Source

All answers are strictly retrieved from: **[The Gale Encyclopedia of Medicine (PDF)](https://github.com/pranav6905/medical_chatbot/blob/main/data/The_GALE_ENCYCLOPEDIA_of_MEDICINE_SECOND.pdf)**  
*A comprehensive medical reference covering thousands of diseases, treatments, and symptoms.*
