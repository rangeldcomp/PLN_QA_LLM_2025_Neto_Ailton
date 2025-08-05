# 🤖 Comparação de Respostas com LLMs usando Documentos

Este projeto avalia a performance de alguns (LLMs) aplicando perguntas e respostas baseada em documentos em formato `.docx` e `.pdf`, comparando as **respostas geradas** com as **respostas esperadas** por meio de duas métricas:

- ✅ **Score do modelo** (confiança da resposta)
- ✅ **Similaridade textual com a resposta esperada** (TF-IDF + Cosseno)

---

## 📁 Estrutura esperada de arquivos

O notebook espera dois arquivos principais (realize o upload ao executar):

- `DICIONARIO_DE_DADOS.docx`: contém tabelas com dados técnicos.
- `doencas_respiratorias_cronicas.pdf`: contém conteúdo textual sobre doenças respiratórias.

---

## 📋 Etapas do processo

1. ### **Instalação de dependências**
   Instala bibliotecas necessárias:
   - `transformers`
   - `docx` (leitura de docx)
   - `pymupdf` (leitura de PDF)
   - `scikit-learn` (para análise de similaridade)

2. ### **Upload dos arquivos**
   É necessário o envio dos arquivos para execução correta do código
   Disponibilizado na pasta content

3. ### **Extração de texto**
   - Do `.docx`: extrai parágrafos e conteúdo de **tabelas**.
   - Do `.pdf`: extrai o conteúdo de cada página.

4. ### **Definição das perguntas e respostas esperadas**
   São feitas 3 perguntas para cada documento. Cada uma tem uma **resposta esperada** definida manualmente.

5. ### **Modelos utilizados**
   Três modelos gratuitos da Hugging Face são usados:
   - `deepset/roberta-base-squad2`
   - `distilbert-base-cased-distilled-squad`
   - `ktrapeznikov/albert-xlarge-v2-squad-v2`

6. ### **Processo de Perguntas e Respostas**
   Para cada modelo e pergunta:
   - É feita uma inferência (`pipeline(question, context)`).
   - A resposta do modelo é salva com:
      - ✅ `Fonte`: source_name,
      - ✅ `Pergunta`: pergunta,
      - ✅ `Modelo`: model_name,
      - ✅ `Resposta do Modelo`: resposta_modelo,
      - ✅ `Score do Modelo`: score,
      - ✅ `Resposta Esperada`: resposta_esperada,
      - ✅ `Similaridade com Esperada`: similaridade


7. ### **Cálculo de Similaridade**
   A similaridade textual entre a resposta do modelo e a resposta esperada é calculada com:
   - `TF-IDF` (vetorização do texto)
   - `Cosine Similarity`

8. ### **Apresentação dos Resultados**
   Os resultados são exibidos em uma tabela contendo:
      - Fonte	
      - Pergunta	
      - Modelo	
      - Resposta do Modelo	
      - Score do Modelo	
      - Resposta Esperada	
      - Similaridade com Esperada