# cureX Medical Chatbot

A specialized medical chatbot built with Llama2 that can answer medical questions based on provided documents. The chatbot uses a vector database to retrieve relevant information and generate accurate responses.

## Features

- Medical Q&A based on uploaded medical documents
- Document ingestion and vectorization
- Semantic search using FAISS vector store
- Conversational UI with Chainlit

## Requirements

- Python 3.8+
- PyPDF for PDF processing
- LangChain for document handling and chains
- Sentence Transformers for embeddings
- FAISS for vector storage
- Chainlit for the user interface
- Hugging Face Hub for model access
- CTransformers for model inference

## Installation

1. Clone the repository:
```bash
git clone https://github.com/purushottamraj2256/cureX.git
cd cureX
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
# On Windows
venv\Scripts\activate
# On Unix or MacOS
source venv/bin/activate
```

3. Install the required packages:
```bash
pip install -r requirements.txt
```

## Usage

### 1. Data Preparation

Place your medical PDF documents in the `data/` directory.

### 2.Download the lamma model

https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML/blob/main/llama-2-7b-chat.ggmlv3.q8_0.bin

### 3. Ingest Documents

Run the ingestion script to process the documents and create the vector database:

```bash
python ingest.py
```

This will:
- Load the PDF documents from the `data/` directory
- Split the documents into chunks
- Generate embeddings for each chunk
- Store the embeddings in a FAISS vector database

### 3. Run the Chatbot

Start the Chainlit application:

```bash
chainlit run model.py
```

The chatbot will be available at http://localhost:8000

## How It Works

1. **Document Processing**: The `ingest.py` script processes PDF documents and creates embeddings.
2. **Vector Database**: Embeddings are stored in a FAISS vector database for efficient retrieval.
3. **Retrieval**: When a query is received, the system finds the most relevant document chunks.
4. **LLM Response**: The Llama2 model generates a response based on the retrieved context.
5. **User Interface**: Chainlit provides a chat interface for interacting with the model.

## Project Structure

- `model.py`: Main application file with Chainlit UI and QA chain
- `ingest.py`: Document processing and vectorization
- `requirements.txt`: Required Python packages
- `data/`: Directory for medical PDF documents
- `vectorstore/`: Contains the FAISS vector database
- `chainlit.md`: Chainlit configuration and welcome message
- `cureX.pdf`: Project documentation and overview

## Documentation
'https://gamma.app/docs/cureX-0dm31aih3z3oa6y'
For a comprehensive overview of the project, please refer to the [cureX.pdf](./cureX.pdf) documentation file. This document contains detailed information about:

- Project architecture and design
- Implementation details
- Usage examples
- Technical specifications

## Customization

You can modify the model parameters in `model.py`:

```python
llm = CTransformers(
    model = "TheBloke/Llama-2-7B-Chat-GGML",
    model_type="llama",
    max_new_tokens = 512,
    temperature = 0.5
)
```

- Increase `max_new_tokens` for longer responses
- Adjust `temperature` for more creative (higher) or deterministic (lower) outputs

## License

MIT License

## Acknowledgements

- [TheBloke](https://huggingface.co/TheBloke) for the Llama2 model quantization
- [LangChain](https://github.com/langchain-ai/langchain) for the document processing framework
- [Chainlit](https://github.com/Chainlit/chainlit) for the chat interface
- [Hugging Face](https://huggingface.co) for the model hosting

## Contact
For support or inquiries, please contact [purushottamraj2256@gmail.com](mailto:purushottamraj2256@gmail.com).
