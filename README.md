
# Substituir Texto em Arquivos `.cmf` no Google Colab

Este projeto mostra como substituir a sigla de uma UF como "RS" por "PA" em todos os arquivos `.cmf` em uma pasta específica no Google Drive e salvar os arquivos modificados em uma nova pasta, usando Python no Google Colab.

## Funcionalidades

- Montagem do Google Drive no Google Colab
- Substituição de texto em arquivos `.cmf`
- Salvamento de arquivos modificados em uma nova pasta

## Pré-requisitos

- Conta no Google
- Acesso ao Google Colab
- Arquivos `.cmf` armazenados no Google Drive

## Como Usar

### Passo 1: Montar o Google Drive

No Google Colab, monte o Google Drive para acessar os arquivos:

```python
from google.colab import drive
drive.mount('/content/drive')
```

### Passo 2: Definir a Função de Substituição de Texto e Salvamento em Nova Pasta

Defina a função para substituir o texto em um arquivo e salvá-lo em uma nova pasta:

```python
import os

def replace_text_in_file(file_path, old_text, new_text, new_folder_path):
    """
    Substitui o texto em um arquivo e salva em uma nova pasta.

    Args:
    file_path (str): O caminho para o arquivo.
    old_text (str): O texto a ser substituído.
    new_text (str): O novo texto.
    new_folder_path (str): O caminho para a nova pasta onde os arquivos modificados serão salvos.
    """
    with open(file_path, 'r', encoding='utf-8') as file:
        content = file.read()
    updated_content = content.replace(old_text, new_text)
    
    # Criar o caminho para o novo arquivo
    new_file_path = os.path.join(new_folder_path, os.path.basename(file_path))
    
    # Salvar o conteúdo atualizado no novo arquivo
    with open(new_file_path, 'w', encoding='utf-8') as file:
        file.write(updated_content)
    print(f'Texto substituído e arquivo salvo em {new_file_path}')
```

### Passo 3: Especificar os Caminhos das Pastas

Especifique o caminho da pasta onde os arquivos `.cmf` estão localizados e o caminho da nova pasta onde os arquivos modificados serão salvos:

```python
# Substitua pelo caminho para a sua pasta no Google Drive
original_folder_path = '/content/drive/My Drive/caminho/para/sua/pasta'
new_folder_path = '/content/drive/My Drive/caminho/para/nova/pasta'

# Criar a nova pasta se ela não existir
os.makedirs(new_folder_path, exist_ok=True)
```

### Passo 4: Listar Todos os Arquivos `.cmf` na Pasta

Liste todos os arquivos `.cmf` na pasta especificada:

```python
# Listar todos os arquivos .cmf na pasta
cmf_files = [os.path.join(original_folder_path, file) for file in os.listdir(original_folder_path) if file.endswith('.cmf')]
```

### Passo 5: Executar a Substituição e Salvar os Arquivos na Nova Pasta

Execute a substituição de "RS" por "PA" em cada arquivo e salve os arquivos modificados na nova pasta:

```python
# Executar a substituição para cada arquivo
for file_path in cmf_files:
    replace_text_in_file(file_path, 'RS', 'PA', new_folder_path)
```

## Contribuição

Sinta-se à vontade para contribuir com melhorias para este projeto. Para isso, siga os passos abaixo:

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Faça o commit das suas alterações (`git commit -m 'Add some AmazingFeature'`)
4. Faça o push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## Licença

Distribuído sob a licença MIT. Veja `LICENSE` para mais informações.

## Contato

Seu Nome - [@vitormarinh0](https://twitter.com/vit0rmarinh0) - vitormarinho@cedeplar.ufmg.br

Link do Projeto: [https://github.com/seu_usuario/seu_projeto](https://github.com/seu_usuario/seu_projeto)

---
