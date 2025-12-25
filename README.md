# Agentic AI Research & Business Insight Agent

An intelligent, autonomous AI agent that analyzes long-form documents and extracts actionable business insights. The agent uses a ReAct (Reasoning + Acting) framework to intelligently decompose complex research goals into manageable steps and execute them using specialized tools.

## Overview

This project implements a sophisticated agentic AI system that goes beyond simple document retrieval. Instead of passively returning search results, the agent actively reasons about your research goals, decides which tools to use, and iteratively works toward comprehensive answers with self-evaluation and confidence scoring.

## Key Features

- **Intelligent Document Analysis**: Upload PDFs and get AI-driven insights tailored to your specific research goals
- **Autonomous Planning**: The agent breaks down complex goals into ordered steps before execution
- **Multi-Tool Reasoning**: Uses specialized tools including document retrieval, summarization, action item extraction, and external research
- **Self-Evaluation**: The agent evaluates its own responses for quality, coherence, and relevance before finalizing
- **Confidence Scoring**: Understand the agent's confidence level in its findings
- **External Research**: Seamlessly integrates external information when document context is insufficient
- **Semantic Search**: FAISS-based vector retrieval for accurate document chunk matching
- **Interactive UI**: User-friendly Streamlit interface for document uploads and goal specification

## Functionality

### Core Components

1. **Document Ingestion & Processing**
   - PDF parsing and extraction
   - Text chunking with configurable overlap
   - Semantic embedding generation

2. **Vector Store & Retrieval**
   - FAISS-based vector database for efficient similarity search
   - Retrieves relevant document chunks based on semantic similarity
   - Configurable retrieval depth (number of chunks)

3. **Agent with Multiple Tools**
   - **Plan Steps**: Decomposes user goals into actionable steps
   - **Retrieve Context**: Fetches relevant document chunks using semantic search
   - **Summarize Context**: Condenses retrieved information into concise summaries
   - **Extract Action Items**: Identifies tasks, recommendations, and next steps
   - **Self-Evaluate**: Assesses response quality and relevance
   - **External Search**: Supplements document findings with external information

4. **LLM Integration**
   - Powered by Groq's fast LLM API (Mixtral model)
   - Efficient inference for real-time analysis

5. **Confidence & Quality Metrics**
   - Automatic confidence scoring of findings
   - Quality assessment of generated insights

## Tech Stack

- **LangChain**: Agent orchestration and tool management
- **Groq API**: High-speed LLM inference (Mixtral-8x7b)
- **FAISS**: Vector similarity search
- **SentenceTransformers**: Semantic embeddings (all-MiniLM-L6-v2)
- **PyPDF**: PDF document parsing
- **Streamlit**: Interactive web UI
- **Python 3.8+**: Core language

## Installation

### Prerequisites
- Python 3.8 or higher
- Groq API key (get one at [Groq Console](https://console.groq.com))

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/Agentic-Research-Analyst.git
   cd Agentic-Research-Analyst
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   ```bash
   # Create a .env file in the root directory
   echo GROQ_API_KEY=your_groq_api_key_here > .env
   ```

## Usage

1. **Start the Streamlit application**
   ```bash
   streamlit run app.py
   ```

2. **Upload a Document**
   - Click "Upload a PDF" and select your document
   - The system will process and ingest the document (chunking and embedding)

3. **Specify Your Research Goal**
   - Enter a clear research goal or question
   - Examples:
     - "Summarize the key findings and provide risks with mitigations"
     - "Extract all financial metrics and recommendations"
     - "What are the main challenges and proposed solutions?"

4. **Run the Agent**
   - Click "Run Agent"
   - The agent will:
     - Plan its approach
     - Retrieve relevant document sections
     - Analyze and synthesize information
     - Evaluate its findings
     - Present the final insights

5. **Review Results**
   - The agent provides a comprehensive, well-reasoned answer
   - All sources are cited
   - Confidence metrics are included

## Project Structure

```
.
├── app.py                    # Main Streamlit application
├── requirements.txt          # Python dependencies
├── README.md                 # This file
├── agent/
│   ├── agent.py              # Agent builder and orchestrator
│   ├── tools.py              # Core agent tools
│   ├── external_tools.py     # External research tool
│   ├── planner.py            # Goal planning module
│   └── evaluator.py          # Response evaluation module
├── rag/
│   ├── ingest.py             # PDF ingestion and chunking
│   ├── embeddings.py         # Embedding generation
│   ├── vector_store.py       # FAISS vector store management
│   └── chunking.py           # Text chunking utilities
├── llm/
│   └── groq_llm.py           # Groq API integration
├── utils/
│   └── confidence.py         # Confidence scoring
└── data/
    └── uploads/              # Uploaded PDF storage
```

## Configuration

You can customize the agent's behavior by setting environment variables:

- `GROQ_API_KEY`: Your Groq API key (required)
- `RETRIEVE_K`: Number of document chunks to retrieve (default: 5)
- `MODEL_NAME`: Groq model to use (default: mixtral-8x7b-32768)

## How It Works: Under the Hood

1. **Document Ingestion**: PDF is parsed, split into overlapping chunks, and converted to semantic embeddings
2. **Query Planning**: Agent analyzes the user's goal and creates a step-by-step plan
3. **Iterative Reasoning**: Agent executes tools in sequence:
   - Retrieves relevant chunks from the vector store
   - Summarizes findings
   - Extracts actionable insights
   - Evaluates quality
4. **External Augmentation**: If needed, the agent supplements with external research
5. **Quality Assurance**: Self-evaluation ensures confidence and relevance
6. **Final Answer**: Grounded, well-reasoned insights with source citations

## Example Use Cases

- **Business Intelligence**: Extract strategic insights from research reports
- **Legal Document Analysis**: Identify key clauses, risks, and obligations
- **Market Research**: Synthesize industry reports into actionable recommendations
- **Academic Research**: Summarize papers and extract key findings
- **Risk Assessment**: Identify potential issues and mitigation strategies
- **Competitive Analysis**: Extract competitor information and market positioning

## Future Enhancements

- Multi-document analysis across multiple PDFs
- Chat history and conversation memory
- Custom tool creation interface
- Performance metrics dashboard
- Export results in multiple formats (PDF, JSON, etc.)
- Advanced filtering and search options

## Troubleshooting

**Issue**: "GROQ_API_KEY not found"
- **Solution**: Ensure you've set the GROQ_API_KEY environment variable in your .env file

**Issue**: "Vector store not initialized"
- **Solution**: Make sure to upload a PDF before entering a research goal

**Issue**: Slow performance
- **Solution**: Reduce the RETRIEVE_K value or use a smaller document

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Support

For questions or support, please open an issue on the GitHub repository.
