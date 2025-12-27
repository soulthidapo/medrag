# 🩺 MedRAG  
## Medical Retrieval-Augmented Generation Chatbot
**MedRAG** is an end-to-end **medical question-answering system** built using **Retrieval-Augmented Generation (RAG)**.  
It combines Large Language Models (LLMs) with a vector database to generate **context-aware, document-grounded medical responses**, reducing hallucinations and improving reliability.

This project demonstrates a complete GenAI pipeline: **document ingestion → embeddings → vector search → LLM → web application → cloud deployment**.

---

## ✨ Features

- 📄 Medical PDF ingestion and text chunking  
- 🔍 Semantic search using vector embeddings  
- 🧠 Context-grounded responses with LLMs  
- 🌐 Interactive chat interface using Flask  
- 🐳 Dockerized and AWS deployment ready  
- 🔐 Secure API key handling via environment variables  

---

## 🏗️ Architecture Overview

```text
Medical PDF
   ↓
Text Chunking & Embeddings
   ↓
Pinecone Vector Database
   ↓
Retriever (LangChain)
   ↓
LLM (GPT)
   ↓
Flask Web Application

# How to run?
### STEPS:

Clone the repository

```bash
git clone https://github.com/soulthidapo/medrag.git
cd medrag
```
### STEP 01- Create a conda environment after opening the repository

```bash
conda create -n medrag python=3.10 -y
```

```bash
conda activate medrag
```


### STEP 02- install the requirements
```bash
pip install -r requirements.txt
```


### Create a `.env` file in the root directory and add your Pinecone & openai credentials as follows:

```ini
PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```


```bash
# run the following command to store embeddings to pinecone
python store_index.py
```

```bash
# Finally run the following command
python app.py
```

Now,
```bash
open up localhost:
```


### Techstack Used:

- Python
- LangChain
- Flask
- GPT
- Pinecone



# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

	
## 3. Create ECR repo to store/save docker image
    - Save the URI: 315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

   - AWS_ACCESS_KEY_ID
   - AWS_SECRET_ACCESS_KEY
   - AWS_DEFAULT_REGION
   - ECR_REPO
   - PINECONE_API_KEY
   - OPENAI_API_KEY
