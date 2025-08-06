# 📊 Projeto: Modelagem Preditiva de Evasão de Clientes de Telecomunicações

Este projeto é uma continuação do projeto anterior de Análise de Evasão de Clientes de Telecomunicações, focando agora em modelagem preditiva com o objetivo de identificar e prever a evasão de clientes (customer churn) utilizando técnicas de aprendizado de máquina.

---
# 🧠 Objetivo
Desenvolver, avaliar e otimizar modelos de machine learning capazes de prever a probabilidade de um cliente evadir, utilizando um dataset previamente tratado e analisado. O foco é encontrar o modelo com melhor performance geral, com destaque para a métrica ROC AUC.

---

## 📁 Etapas Realizadas

### 🔍 1. Extração de Dados
- Carregamento dos dados tratados a partir do arquivo:  
  `/content/dados_tratados.csv`
- Armazenamento em um DataFrame do Pandas.

---

### 🛠️ 2. Transformação de Dados
- Tradução dos nomes das colunas para o português para maior clareza.
- Tradução dos valores de colunas categóricas (ex: `Gênero`, `Evasão`, `É_Idoso`, etc.).
- Remoção da coluna `ID_Cliente` (identificador único, sem valor preditivo direto).
- Aplicação de **One-Hot Encoding** para variáveis categóricas (`pd.get_dummies()`), com `drop_first=True` para evitar multicolinearidade.
- Conversão das colunas booleanas resultantes para tipo inteiro (0 ou 1).

---

### 📊 3. Análise Exploratória (EDA)

ℹ️ Informações Básicas
- Checagem de tipos de dados, valores nulos e contagem por coluna.

📈 Proporção de Evasão
- A classe alvo `Evasão_Sim` apresenta cerca de 26,6% de clientes evadidos, sem desequilíbrio severo.

🔍 Análises Visuais
- Matriz de Correlação para identificar variáveis com maior influência na evasão.
- Boxplots:
`Tipo_Contrato` vs. `Meses_de_Serviço` por `Evasão`.
- Scatter Plot:
`Cobranças_Totais` vs. `Meses_de_Serviço` por `Evasão`.

---

### 🧪 4. Preparação para Modelagem
- Separação dos dados:
  - `X_treino`, `X_teste`, `y_treino`, `y_teste`
  - Proporção: 80% treino / 20% teste
  - Uso de estratificação pela variável alvo (`Evasão_Sim`) para manter a proporção em ambos os conjuntos.

---

### 🤖 5. Modelagem Preditiva

### Modelos Treinados:

1. **Dummy Classifier (linha de base)**
2. **Árvore de Decisão (DecisionTreeClassifier)**
3. **Random Forest (RandomForestClassifier)**
 
---

### 📈 6. Avaliação Inicial dos Modelos

#### 🔬 Métricas utilizadas:
- **Acurácia**
- **Precisão**
- **Recall**
- **F1-Score**
- **ROC AUC**
- **Matriz de Confusão**

> Resultado:  
✅ **Random Forest** apresentou melhor desempenho geral.  
⚠️ **Dummy Classifier** teve alta acurácia, mas isso se deve ao desequilíbrio leve na base.  
⚠️ **Decision Tree** teve desempenho inferior e possível overfitting.

---

## 🔧 7. Otimização do Modelo Random Forest

- Definição de uma **grade de hiperparâmetros**.
- Utilização de **GridSearchCV** com validação cruzada (`cv=5`) e métrica `roc_auc`.
- Retreinamento do modelo com os **melhores hiperparâmetros encontrados**.

---

### ✅ 8. Avaliação do Modelo Otimizado

Comparação entre modelo **Random Forest Inicial** e **Random Forest Otimizado**:

| Métrica       | Inicial     | Otimizado  |
|---------------|-------------|------------|
| Acurácia      | 0.7953      | 0.7982     |
| Precisão      | 0.6514      | 0.6630     |
| Recall        | 0.4947      | 0.4893     |
| F1-Score      | 0.5623      | 0.5631     |
| ROC AUC       | 0.8261      | **0.8481** |

> ⚠️ Ligeira **redução no Recall**, indicando que o modelo otimizando identificou **um pouco menos** clientes que realmente evadiram, mas teve **melhora significativa na capacidade discriminativa (ROC AUC)**.

---

## 💡 Conclusões e Insights

- O modelo **Random Forest otimizado** se mostrou o **mais eficaz** para prever a evasão de clientes.
- A **otimização de hiperparâmetros** trouxe ganhos reais nas métricas principais, especialmente **ROC AUC**, que passou de **0.8261 para 0.8481**.
- A **alta acurácia do modelo Dummy** mostra que nem sempre essa métrica é confiável sozinha, especialmente em problemas com classes desbalanceadas.
- A visualização da **matriz de correlação** e os **gráficos exploratórios** foram essenciais para obter insights iniciais sobre variáveis com maior influência na evasão.
- Este modelo pode ser utilizado para **identificar clientes com alta probabilidade de evasão** e permitir ações proativas de retenção por parte da empresa.

---

## 📍 Próximos Passos (Sugeridos)

- Aplicar técnicas de **balanceamento de classes** (SMOTE, undersampling) para tentar aumentar o Recall.
- Testar **outros algoritmos** (XGBoost, LightGBM, etc.).
- Implementar um **painel de monitoramento** para avaliar métricas de evasão em tempo real.

---

## 🧰 Ferramentas Utilizadas

- Python 3.10+
- Google Colab
- Pandas, Numpy
- Scikit-learn (sklearn)
- Matplotlib / Seaborn
- GridSearchCV
- Train/Test Split com estratificação

---

## 🚀 Como Executar

1. Clone o repositório:
   ```bash
   git clone git@github.com:pedrohalarcao/projeto-telecom-ml.git
   cd projeto-telecom-ml

---

## 👤 Autor

Pedro Alarcão

Entusiasta em Ciência de Dados e Inteligência Artificial, com foco em aplicações práticas para tomada de decisão estratégica.

---

## 📝 Licença

Este projeto está licenciado sob os termos da licença MIT. Consulte o arquivo LICENSE para mais informações.

