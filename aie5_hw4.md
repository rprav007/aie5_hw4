# Questions and Answers

1. What other models could we use, and how would the above code change?

   There are other models that is offered by and they can be found at https://platform.openai.com/docs/models. Here are a few listed:
   * gpt-4o
   * gpt-4o mini
   * o1
   * o1-mini

   We can change the name of the model in this line in order to use a different model openai_chat_model = ChatOpenAI(model="gpt-4o-mini")

2. What is the embedding dimension, given that we're using `text-embedding-3-small`?

   For the text-embedding-3-small the default value is 1536

3. Brainstorm some ideas that would split large single documents into smaller documents.

   Here are some of the chunking strategies, each have their pros and cons and it squarely depends on the use case
   * Fixed size chunking
   * Sentence based
   * Paragraph based
   * Overlap chunking
   * Semantic chunking
  
4. LangGraph's graph-based approach lets us visualize and manage complex flows naturally. How could we extend our current implementation to handle edge 
   cases? For example:
     - What if the retriever finds no relevant context?  
     - What if the response needs fact-checking?
  Consider how you would modify the graph to handle these scenarios.

  * What if the retriever finds no relevant context?

    We should first make sure the context retrieved was really null or is that wrong interpretation, a simple conditional check. If there really was
    no context then we can go back to the user with a graceful message that there was no context found instead of a blank "I dont know". Alternatively
    we can ask more questions to derive context in subsequent iterations or see if there are any alternate RAG sources.

  * What if the response needs fact-checking?

    Have a final catch all path to make sure all answers go through a very powerful and accurate LLM before the final output is returned.
  
5. What does LCEL do that makes it more reliable at scale?

   LCEL provides several features that enhance reliability at scale. It allows for graceful error handling through fallbacks, which is crucial
   due to the non-determinism of LLMs. Additionally, LCEL supports parallelism, enabling components to run in parallel and improving overall
   efficiency, especially during potentially long API calls. These features contribute to making LCEL more reliable when deployed at scale.
   

