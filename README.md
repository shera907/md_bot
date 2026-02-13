# MD_Bot

A conversational AI chatbot application that processes PDF documents and answers questions about their content using retrieval-augmented generation (RAG).

## Features

- **PDF Processing**: Upload and extract text from PDF documents
- **Semantic Search**: Uses FAISS vector store with HuggingFace embeddings to find relevant content
- **Intelligent Chat Interface**: Ask questions about your PDF documents and get AI-powered responses
- **Interactive UI**: Built with Streamlit for an intuitive, responsive user interface
- **Multi-file Support**: Process multiple PDF files simultaneously
- **Context-Aware Responses**: Leverages document content for accurate and relevant answers

## Prerequisites

- Python 3.11 or higher
- pip (Python package manager)
- A valid EURI API key for chat model access

## Installation

1. **Clone the repository** (or navigate to the project directory)
   ```bash
   cd c:\AI_Projects\Projects\MD_Bot
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Configuration

Before running the application, ensure your API key is configured:

1. Open `app/config.py`
2. Set your EURI API key:
   ```python
   EURI_API_KEY = "your-api-key-here"
   ```

## Usage

1. **Start the application**
   ```bash
   streamlit run main.py
   ```

2. **Open in your browser**
   - Streamlit will automatically open the application (usually at `http://localhost:8501`)

3. **Upload PDF files**
   - Use the file uploader in the sidebar to select one or more PDF files
   - Click upload to process the documents

4. **Ask questions**
   - Type your questions about the PDF content in the chat interface
   - The chatbot will search the documents and provide relevant answers

## Project Structure

```
MD_Bot/
├── main.py                      # Main application entry point
├── requirements.txt             # Project dependencies
├── README.md                    # Project documentation
├── sample_data/                 # Sample PDF files for testing
└── app/
    ├── __init__.py
    ├── config.py               # Configuration and API keys
    ├── chat_utils.py           # Chat model initialization and queries
    ├── pdf_utils.py            # PDF text extraction utilities
    ├── ui.py                   # Streamlit UI components
    └── vectorstore_utils.py    # FAISS vector store and similarity search
```

## Dependencies

The project uses the following key libraries:

| Library | Purpose |
|---------|---------|
| **Streamlit** | Web UI framework for the application |
| **LangChain** | LLM integration and text processing |
| **FAISS** | Vector similarity search and indexing |
| **Sentence Transformers** | Generate embeddings for semantic search |
| **PyPDF** | PDF reading and text extraction |
| **fpdf** | PDF generation support |
| **euriai** | Chat model API client |

## How It Works

1. **Document Upload**: Users upload PDF files through the Streamlit interface
2. **Text Extraction**: The system extracts text from the PDF documents
3. **Text Splitting**: Long documents are split into manageable chunks using recursive character splitting
4. **Vectorization**: Text chunks are converted to embeddings using HuggingFace's sentence transformers
5. **Indexing**: Embeddings are stored in a FAISS index for efficient similarity search
6. **Query Processing**: User questions are converted to embeddings and matched against the document index
7. **Response Generation**: Relevant document chunks are sent to the EURI chat model to generate contextual answers

## Common Issues

- **API Key Error**: Ensure your EURI_API_KEY is correctly set in `app/config.py`
- **Module Import Errors**: Verify all dependencies are installed with `pip install -r requirements.txt`
- **PDF Upload Issues**: Ensure PDF files are valid and not corrupted

## Future Enhancements

- Persist vector store for faster subsequent queries
- Support for additional document formats (DOCX, TXT, etc.)
- User session management and chat history
- Document chunking strategy optimization
- Web search integration for out-of-document queries

## License

This project is provided as-is for educational and development purposes.

## Contact & Support

For issues or questions, please check the project documentation or create an issue in the repository.
