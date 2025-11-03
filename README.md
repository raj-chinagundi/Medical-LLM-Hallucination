# Group 4 - CSE 543 Medical LLM Hallucination Detection and Evaluation

A comprehensive evaluation framework for comparing Large Language Models (LLMs) in medical question-answering tasks, with a focus on detecting and measuring hallucinations using Retrieval-Augmented Generation (RAG).

## GROUP MEMBERS:

1)Mridul
2)Mehek
3)Basavraj
4)Ajesh
5)Kanish
6)Vaibhav

## Overview

This project implements an automated evaluation pipeline to compare **Google Gemini** and **Llama 3** models in generating medical advice responses. The system uses a hybrid retrieval approach combining BM25 and FAISS vector similarity to ground responses in factual medical literature from PubMed.

## Key Features

- **Dual Model Comparison**: Evaluates both Gemini and Llama 3 models side-by-side
- **Hybrid RAG System**: Combines BM25 keyword matching and FAISS semantic search for optimal document retrieval
- **Multi-dimensional Evaluation**: Assesses responses across multiple critical metrics:
  - Correctness
  - Hallucination Detection
  - Completeness
  - Faithfulness to source documents
  - Groundedness in factual information
  - Empathy in responses
- **PubMed Integration**: Retrieves verified medical literature for grounding responses
- **Comprehensive Visualization**: Generates detailed plots and analysis of model performance

## Project Structure

```
.
├── project_implementation_final.ipynb  # Main implementation notebook
├── capstone_results.csv                # Complete evaluation results
├── sample_responses.csv                # Sample responses from both models
└── results/
    ├── comparison_all_document_scores.csv
    ├── comparison_capstone_results.csv
    ├── plot1_boxplot.png              # Distribution of scores
    ├── plot2_stripplot.png            # Individual score comparisons
    ├── plot3_radar.png                # Multi-metric radar chart
    ├── plot4_heatmap.png              # Correlation heatmap
    ├── plot5_empathy_faithfulness.png # Empathy vs Faithfulness analysis
    └── plot6_bar_comparison.png       # Metric comparison bars
```

## Methodology

### 1. Document Retrieval
- Fetches relevant medical articles from PubMed using Entrez API
- Scrapes full-text content when available
- Implements hybrid scoring combining:
  - BM25 keyword matching
  - FAISS semantic similarity
  - Title and full-text matching

### 2. Response Generation
- Generates responses using both Gemini and Llama 3 models
- Uses carefully crafted prompts emphasizing empathy and evidence-based advice
- Implements RAG to ground responses in retrieved documents

### 3. Evaluation System
Uses a separate Gemini model as an evaluator to score responses on:
- **Correctness**: Accuracy of medical information (1-10)
- **Hallucination**: Absence of unsupported facts (10 = no hallucinations)
- **Completeness**: Thoroughness of the response (1-10)
- **Faithfulness**: Adherence to source documents (1-10)
- **Groundedness**: Factual basis of information (1-10)
- **Empathy**: Compassion and understanding in tone (1-10)

## Requirements

```bash
pip install google-generativeai langchain-google-genai ollama pandas numpy
pip install beautifulsoup4 biopython rank_bm25 langchain langchain-community
pip install faiss-cpu lxml matplotlib seaborn evaluate bert_score rouge_score
```

## Usage

1. Set up your NCBI Entrez email in the notebook
2. Configure your Google API key for Gemini access
3. Install and run Ollama for Llama 3 local inference
4. Run the notebook cells sequentially to:
   - Generate responses for medical queries
   - Evaluate responses across all metrics
   - Generate visualization plots

## Results

The evaluation results demonstrate comparative performance between Gemini and Llama 3 across all metrics, with detailed visualizations showing:
- Score distributions
- Metric correlations
- Empathy vs. factual accuracy trade-offs
- Overall model strengths and weaknesses

## Models Used

- **Gemini (Google)**: Cloud-based generative AI model
- **Llama 3**: Open-source model run locally via Ollama
- **Evaluation Model**: Gemini for automated response scoring
