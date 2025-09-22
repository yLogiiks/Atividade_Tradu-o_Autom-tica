# 9.5.7. Exercícios

1. Tente valores diferentes do argumento `num_examples` na função `load_data_nmt`. Como isso afeta os tamanhos do vocabulário do idioma de origem e do idioma de destino?

```python
for num_examples in [100, 300, 600, 1000]:
    _, src_vocab_tmp, tgt_vocab_tmp = load_data_nmt(batch_size=2, num_steps=8, num_examples=num_examples)
    print(f'num_examples={num_examples}: src_vocab={len(src_vocab_tmp)}, tgt_vocab={len(tgt_vocab_tmp)}')
```

num_examples=100: src_vocab=40, tgt_vocab=37  
num_examples=300: src_vocab=102, tgt_vocab=103  
num_examples=600: src_vocab=184, tgt_vocab=195  
num_examples=1000: src_vocab=266, tgt_vocab=313  

Quanto maior o valor de `num_examples` passado para `load_data_nmt`, mais frases são usadas para construir os vocabulários `src_vocab` e `tgt_vocab`. Isso faz com que os tamanhos dos vocabulários aumentem, pois mais palavras diferentes aparecem no conjunto de dados. Com menos exemplos, menos palavras distintas são vistas, resultando em vocabulários menores.

2. O texto em alguns idiomas, como chinês e japonês, não tem indicadores de limite de palavras (por exemplo, espaço). A tokenização em nível de palavra ainda é uma boa ideia para esses casos? Por que ou por que não?

Em idiomas como chinês e japonês, não há espaços para separar palavras, então a tokenização em nível de palavra não é uma boa ideia sem um pré-processamento específico. Nesses casos, é comum usar tokenização em nível de caractere ou aplicar algoritmos de segmentação de palavras, pois a separação correta depende do contexto e do significado. A tokenização em nível de palavra pode causar erros de segmentação e dificultar o processamento do texto nesses idiomas.
