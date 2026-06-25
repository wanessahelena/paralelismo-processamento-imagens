# Processamento de Imagens com Paralelismo e Vetorização no Dataset EuroSAT

Este repositório apresenta um trabalho desenvolvido para a disciplina de **Programação Paralela e Distribuída** do curso de **Engenharia de Computação do IFMG – Campus Bambuí**.

O projeto realiza o processamento de imagens do dataset **EuroSAT** e compara o desempenho de diferentes abordagens de execução:

* **Execução sequencial**
* **Execução paralela com multiprocessing**
* **Execução vetorizada com NumPy**

O objetivo é analisar o ganho de desempenho obtido com técnicas de paralelismo e vetorização em um pipeline de processamento de imagens.

---

## Objetivo

O trabalho tem como objetivo implementar e comparar diferentes estratégias de processamento de imagens, medindo o tempo de execução e avaliando métricas como:

* **Tempo total de processamento**
* **Speedup**
* **Eficiência**

A análise foi realizada utilizando um subconjunto de **2.000 imagens** do dataset **EuroSAT**.

---

## Dataset utilizado

Foi utilizado o dataset **EuroSAT**, composto por imagens de satélite organizadas em diferentes classes de cobertura do solo.

No notebook, o dataset é baixado diretamente via **Kaggle API**.

---

## Etapas do projeto

O notebook está dividido em quatro fases principais:

### **Fase 1 — Preparação**

Nesta etapa foi realizada a preparação do ambiente e dos dados:

* download e extração do dataset EuroSAT;
* leitura das classes disponíveis;
* listagem dos caminhos das imagens;
* seleção de **2.000 imagens** para os experimentos;
* criação da pasta de saída para armazenar as imagens processadas.

---

### **Fase 2 — Execução Sequencial (Baseline)**

Foi implementada uma função de processamento de imagens contendo o pipeline:

1. **Leitura da imagem**
2. **Conversão para escala de cinza**
3. **Aplicação de filtro Gaussiano**
4. **Detecção de bordas com Canny**
5. **Salvamento da imagem processada**

---

### **Fase 3 — Execução Paralela com Multiprocessing**

Nesta etapa, o processamento das imagens foi distribuído entre múltiplos processos utilizando a biblioteca `multiprocessing`.

Foram testadas as seguintes configurações:

* **2 processos**
* **4 processos**
* **6 processos**
* **8 processos**

Para cada configuração, foram calculadas as métricas de desempenho:

* **Tempo total de execução**
* **Speedup**
* **Eficiência**

---

### **Fase 4 — Comparação com Vetorização (NumPy)**

Além da abordagem com múltiplos processos, também foi implementada uma versão vetorizada utilizando **NumPy**.

Nessa etapa, as imagens são carregadas em lote e processadas com operações vetorizadas, buscando comparar o desempenho dessa estratégia com:

* a execução sequencial;
* a melhor configuração do multiprocessing.

---

## Pipeline de processamento de imagem

O pipeline aplicado em cada imagem é composto pelas seguintes operações:

* conversão para **escala de cinza**;
* aplicação de **filtro Gaussiano**;
* **detecção de bordas**.

As imagens processadas são salvas em uma pasta de saída para posterior inspeção.

---

## Gráficos gerados

O notebook gera gráficos para análise comparativa entre as abordagens, incluindo:

* **Tempo total × número de processos**
* **Speedup × número de processos**
* **Eficiência × número de processos**
* **Comparação final entre execução sequencial, multiprocessing e vetorização**

Os gráficos são salvos na pasta:

```bash
results/
```

---

## Tecnologias e bibliotecas utilizadas

* **Python**
* **OpenCV**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Multiprocessing**
* **SciPy**
* **Kaggle API**

---

## Como executar o projeto

### 1. Clone este repositório

```bash
git clone https://github.com/wanessahelena/paralelismo-processamento-imagens.git
cd paralelismo-processamento-imagens
```

### 2. Instale as dependências

Exemplo de instalação das principais bibliotecas:

```bash
pip install opencv-python-headless kaggle numpy pandas matplotlib scipy
```

### 3. Configure a API do Kaggle

Para que o notebook consiga baixar o dataset, é necessário possuir o arquivo `kaggle.json` da sua conta do Kaggle.

No notebook, esse arquivo é copiado para a pasta correta antes do download do dataset.

### 4. Execute o notebook

Abra o arquivo `.ipynb` em um ambiente como:

* **Jupyter Notebook**
* **Google Colab**

e execute as células em ordem.

## Autoria

Projeto desenvolvido por **Wanessa Helena** como trabalho da disciplina de Programação Paralela e Distribuída.

---
