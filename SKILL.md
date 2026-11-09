---
name: abnt-latex-skill
description: Monta trabalhos acadêmicos (TCC, monografia) em LaTeX com a classe facom-ufu-abntex2 (abntex2) seguindo as normas ABNT, pronto para compilar no Overleaf. Use quando o usuário pedir formatação ABNT, modelo de TCC em LaTeX ou projeto para Overleaf.
---

# ABNT em LaTeX (facom-ufu-abntex2)

## Quando usar

- Pedido de trabalho acadêmico em LaTeX com normas ABNT.
- Pedido de projeto para Overleaf.
- Conversão de texto (Markdown ou rascunho) para a estrutura ABNT.

## Insumos que o usuário precisa fornecer

1. **Classe da instituição:** `facom-ufu-abntex2.cls` (FACOM-UFU), incluída em `templates/`. É a classe que define capa, folha de rosto e formatação. Ela é redistribuída sem alterações sob a licença LPPL 1.3; o cabeçalho do arquivo deve ser mantido. Para outra instituição, substitua a classe e revise capa e folha de aprovação.
2. **Dados:** autor, orientador, título, ano, palavras-chave e resumo.

## Fluxo

1. **Coletar os dados.** Pergunte autor, orientador, título, ano, palavras-chave e resumo. Não invente nada.
2. **Copiar o modelo.** Copie a pasta `templates/` inteira (inclui `main.tex`, `capitulos/`, `references.bib` e `facom-ufu-abntex2.cls`). Os arquivos devem ficar na mesma pasta: a classe deve estar na raiz do projeto, ao lado do `main.tex`.
3. **Preencher o `main.tex`.** Substitua os campos entre colchetes: `\autor`, `\data`, `\orientador`, `\titulo`, `\hypersetup` e a data da folha de aprovação.
4. **Escrever os capítulos.** Cada capítulo vai em `capitulos/` e entra com `\input`. Os capítulos de exemplo são do trabalho de referência e devem ser substituídos.
5. **Citações.** Use `\cite{chave}` (entre parênteses) ou `\citeonline{chave}` (`Autor (ano)`). As chaves ficam em `references.bib`.
6. **Compilar.** Gere um `.zip` da pasta do projeto e importe no Overleaf (New Project → Upload Project). Compile com pdfLaTeX.

## Regras da classe (validadas no Overleaf)

- Opções: `12pt, openright, oneside, a4paper, brazilian` (use `brazilian`, não `brazil`).
- Comandos de capa e folha de rosto: `\imprimircapa`, `\imprimirfolhaderosto` (com `folha`, sem `d`).
- Sumário: `\pdfbookmark[0]{\contentsname}{toc}`, `\tableofcontents*`, `\cleardoublepage`. Não existe `\sumario`.
- Folha de aprovação: ambiente `folhadeaprovacao` com `\assinatura{...}`.
- Lista de siglas: ambiente `siglas` com `\item[SIGLA] descrição`.
- Os títulos de capítulo saem em maiúsculas pela classe; não formate manualmente.

## Regras para o `.bib`

- Acentos em LaTeX, não em UTF-8 puro: `Corr{\^e}a`, `Tomi{\'c}`, `gest{\~a}o`, `{\c{c}}`.
- Toda entrada precisa de `year` (use `s.d.` se não houver data).
- Não use `@monography` nem `@online`: use `@misc`, `@book`, `@article`, `@phdthesis`, `@inproceedings`.

## Regras para referências cruzadas

- Não coloque `\label` em `\subsection*` nem em `\section*`. Se precisar referenciar uma seção, use o número fixo (`seção 4.3`) ou `\label` em seção numerada.

## Avisos que podem ser ignorados

- `Package babel Warning: Name 'brazil' is deprecated`: vem da própria `abntex2`.
- `Class memoir Warning: \settocpreprocessor is marked deprecated`: vem da própria `abntex2`.

## Regras gerais

- Não abstraia o conteúdo do trabalho. A skill monta a estrutura; o texto é do autor.
- Não cite fontes sem verificação. Entradas sem ano ou fonte primária ficam marcadas como `[a confirmar]`.
- Escape caracteres especiais no texto: `\_`, `\%`, `\&`, `\#`, `\$`.
- Glossário, se houver, fica depois das referências.

## Limites

- Os modelos ainda não foram compilados localmente: a compilação deve ser conferida no Overleaf.
- A classe é da FACOM-UFU. Para outra instituição, substitua a classe e revise capa e folha de aprovação.
