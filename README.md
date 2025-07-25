---
# Loan Approval RAG Chatbot using LangChain + Ollama (Local LLM)

A Retrieval-Augmented Generation (RAG) based chatbot that answers questions about loan eligibility and approvals, using a local LLM via Ollama and LangChain. It loads your own loan training data, embeds it, and allows intelligent Q&A using vector search.

---

**Key Point** : Please go through "Example.ipynb", it has a very detailed explanation of how a RAG model works as a model and on different kinds of data like pdf, txt, etc.

---

##  Project Structure

```

loan-rag-chatbot/
├── Train.txt                 # Training data (raw text format for RAG)
├── app.py                   # Main chatbot code
├── db/                      # Persistent Chroma vector DB 

````

---

##  Features

 Local LLM using [Ollama](https://ollama.com/)  
 Embeddings with `all-MiniLM-L6-v2` from HuggingFace  
 Chunked document processing with LangChain  
 Vector search using ChromaDB
 Custom prompt with context-aware responses  
 Answers only from your documents (`Train.txt`)

---

##  Setup Instructions

### 1.  Install Requirements
```bash
pip install langchain langchain-community langchain-huggingface langchain-ollama chromadb sentence-transformers
````

Also install Ollama and start the model:

```bash
ollama run llama3
```

### 2.  Place your data

Put your `Train.txt` in the same dir.

### 3.  Run the chatbot

```bash
python RAG.ipynb
```

---

## What’s Happening Under the Hood?

1. **Load your training data** using `TextLoader`.
2. **Split it into chunks** using `RecursiveCharacterTextSplitter`.
3. **Create embeddings** using `sentence-transformers/all-MiniLM-L6-v2`.
4. **Store them in Chroma** for vector-based retrieval.
5. **Load the Ollama LLM (like LLaMA3)** locally.
6. **Use RetrievalQA from LangChain** to fetch and answer queries.
7. **Display sources used** for transparency.

---

## Notes

* This is a **local RAG app**: No API key required.
* Works **offline once Ollama model is downloaded**.
* Update or change the `Train.txt` file to adapt it to your own data.

---
