# Análise de Complexidade de Algoritmos: Como a Eficiência Impacta o Desempenho

Material didático desenvolvido para o ensino de Análise de Algoritmos e Estrutura de Dados, explorando a relação entre complexidade de tempo, recursos computacionais e escalabilidade por meio da **Notação Big-O** com exemplos práticos em Python.

---

## O que determina a eficiência de um algoritmo?

A eficiência de um algoritmo está diretamente ligada à forma como ele utiliza recursos computacionais, especialmente **tempo de execução** e **uso de memória (espaço)**, conforme o volume de dados de entrada ($N$) cresce.

* **Algoritmos Eficientes:** Resolvem o problema consumindo a menor quantidade viável de recursos, escalando bem mesmo com entradas massivas. Comumente associados a complexidades $O(1)$, $O(\log n)$, $O(n)$ e $O(n \log n)$.
* **Algoritmos Ineficientes:** Consomem tempo ou memória de forma desproporcional. Tornam-se inviáveis à medida que a entrada aumenta, como complexidades $O(n^2)$, $O(2^n)$ ou $O(n!)$.

---

## Tabela Comparativa de Complexidade (Big-O)

| Notação | Classificação | Comportamento com o aumento de $N$ | Exemplo Clássico |
| :---: | :---: | :--- | :--- |
| **$O(1)$** | Constante | Execução instantânea; independente de $N$. | Acesso direto por índice em array. |
| **$O(\log n)$** | Logarítmica | Cresce muito lentamente; divide o problema pela metade. | Busca Binária. |
| **$O(n)$** | Linear | Cresce proporcionalmente ao tamanho da entrada. | Busca Linear (varredura). |
| **$O(n \log n)$** | Quase Linear | Padrão ótimo para ordenações por comparação. | Merge Sort, Quick Sort (médio). |
| **$O(n^2)$** | Quadrática | Tempo cresce rapidamente; inviável para grandes volumes. | Bubble Sort, laços aninhados. |
| **$O(n!)$** | Fatorial | Crescimento explosivo; inviável computacionalmente. | Caixeiro-viajante por força bruta. |

---

## Exemplos Práticos em Python

### 1. $O(1)$ — Complexidade Constante
O tempo de execução não depende do tamanho da entrada.
```python
def obter_primeiro_elemento(lista):
    return lista[0]
```
> **Vantagem:** Muito eficiente. Ideal sempre que possível.

---

### 2. $O(\log n)$ — Complexidade Logarítmica
O tempo de execução cresce lentamente conforme a entrada aumenta, pois o espaço de busca é reduzido pela metade a cada passo.
```python
def busca_binaria(lista, alvo):
    inicio, fim = 0, len(lista) - 1
    while inicio <= fim:
        meio = (inicio + fim) // 2
        if lista[meio] == alvo:
            return True
        elif lista[meio] < alvo:
            inicio = meio + 1
        else:
            fim = meio - 1
    return False
```
> **Aplicação:** Essencial para buscas eficientes em grandes volumes de dados ordenados.

---

### 3. $O(n)$ — Complexidade Linear
O tempo de execução cresce proporcionalmente ao tamanho da lista.
```python
def encontrar_valor(lista, valor):
    for item in lista:
        if item == valor:
            return True
    return False
```
> **Característica:** Precisa verificar cada elemento pelo menos uma vez no pior caso.

---

### 4. $O(n \log n)$ — Complexidade Quase Linear
Tempo ligeiramente superior ao linear, mas amplamente aceito como o limite eficiente para ordenação baseada em comparação.
```python
def merge_sort(lista):
    if len(lista) <= 1:
        return lista
    
    meio = len(lista) // 2
    esquerda = merge_sort(lista[:meio])
    direita = merge_sort(lista[meio:])
    
    return merge(esquerda, direita)

def merge(esq, dir):
    resultado = []
    i = j = 0
    while i < len(esq) and j < len(dir):
        if esq[i] < dir[j]:
            resultado.append(esq[i])
            i += 1
        else:
            resultado.append(dir[j])
            j += 1
    resultado.extend(esq[i:])
    resultado.extend(dir[j:])
    return resultado
```
> **Aplicação:** Algoritmos eficientes de ordenação para grandes coleções de dados.

---

### 5. $O(n^2)$ — Complexidade Quadrática
O tempo de execução cresce de forma proporcional ao quadrado da entrada. Torna-se lento rapidamente para entradas a partir de centenas de itens.
```python
def verificar_duplicados(lista):
    for i in range(len(lista)):
        for j in range(i + 1, len(lista)):
            if lista[i] == lista[j]:
                return True
    return False
```
> **Alerta:** Comum em algoritmos ingênuos de força bruta com laços de repetição aninhados.

---

### 6. $O(n!)$ — Complexidade Fatorial
Crescimento explosivo. Para $N = 10$, já são necessárias mais de 3,6 milhões de operações.
```python
import itertools

def gerar_permutacoes(lista):
    return list(itertools.permutations(lista))
```
> **Limitação:** Computacionalmente impraticável para valores de $N$ moderados ou grandes.

---

## Conclusão

Avaliar a complexidade assintótica de um algoritmo permite tomar decisões conscientes de arquitetura de software, prevenindo gargalos de desempenho e consumo desnecessário de infraestrutura antes mesmo de colocar a solução em produção.

---

## Autoria
* **Profª Rebeca** — Professora de Computação
* Material desenvolvido para suporte às aulas de Algoritmos e Estrutura de Dados.

---

## Gráfico de Complexidade

<p align="center">
  <img width="860" height="610" alt="image" src="https://github.com/user-attachments/assets/83f42015-b69e-4a38-9b03-1028e0156033" />
</p>
