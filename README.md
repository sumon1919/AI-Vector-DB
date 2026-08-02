# AI-Controlled Vector Memory Workflow
(./images/workflow.png)
An AI-powered memory workflow built with **n8n, Ollama, and Qdrant**.

### Features

* 🧠 AI decides whether a request needs **Direct processing or Memory**
* 🔎 Semantic **vector search** using Qdrant
* ➕ Automatically **insert** new information into memory
* 🗑️ **Delete** specific stored information
* 🎯 Similarity score validation before deleting/searching data
* 🤖 Uses Ollama for local AI and embeddings
* 💾 Qdrant works as the long-term vector memory
* 🔀 Automated routing for **Search / Insert / Delete**
* 🔒 Can run locally without relying on external AI APIs

## Installation

### 1. Install n8n

```bash
npm install -g n8n
```

Start n8n:

```bash
n8n start
```

### 2. Install Ollama

Install Ollama and pull the required models:

```bash
ollama pull qwen2.5:3b
ollama pull nomic-embed-text
```

Make sure Ollama is running.

### 3. Run Qdrant

Using Docker:

```bash
docker run -p 6333:6333 qdrant/qdrant
```

Create a Qdrant collection named:

```text
memory
```

The vector size should match the embedding model output.

### 4. Import the Workflow

Import the provided `.json` workflow into n8n.

Then configure:

* Ollama URL
* Qdrant URL
* Qdrant collection name
* Required credentials/tools

### Architecture

```text
User
 ↓
AI Planner
 ↓
Direct / Memory
 ↓
Search / Insert / Delete
 ↓
Ollama Embeddings
 ↓
Qdrant Vector Database
 ↓
AI Response
```

> This project is designed as a reusable AI memory layer for AI agents, assistants, customer support systems, RAG applications, and automation workflows.

