# Praimos — gerador de sites e sistemas web

Skill em português baseada nos projetos corretos de blog e loja Praimos. Inclui instruções, presets visuais, contratos por produto e um gerador estático sem dependências para sete tipos de site.

## Instalar

Baixe `praimos-site-generator.zip` neste repositório e extraia. Copie a pasta `praimos-site-generator` para `~/.codex/skills/` (Windows: `%USERPROFILE%\.codex\skills\`). Invoque `$praimos-site-generator` com seu briefing ou peça ao agente para ler `SKILL.md` pelo caminho. A instalação global não é feita automaticamente por este pacote.

Exemplo: “Use $praimos-site-generator para criar um blog sobre jogos, com tema Praimos, três artigos e busca”.

## Gerar uma base local

Requer Python 3.10+; sem instalação de pacotes nem acesso à rede. Execute na pasta da skill:

```sh
python scripts/generate.py --type blog --name "Praimos Journal" --output ../meu-blog
python scripts/generate.py --type loja --name "Praimos Store" --preset loja --theme claro --output ../minha-loja
python -m http.server 4173 --bind 127.0.0.1 --directory ../meu-blog
```

Abra http://127.0.0.1:4173. Tipos: blog, loja, plataforma, vendas, software, institucional, landing. O diretório pai deve existir e o destino deve não existir: o gerador nunca sobrescreve um projeto. Nomes são escapados como texto. Para interromper o servidor, use Ctrl+C no terminal que o iniciou.

```sh
python scripts/test_generator.py
node --check assets/app.js
```

Os sites são protótipos locais identificados: sem pagamento, login, banco ou envio de formulário. Carrinho e tarefas ficam em memória e zeram no reload. A skill orienta evolução e verificação de integrações reais separadamente. Não promete gerar um SaaS em produção com uma única execução do script.

## Estrutura

`SKILL.md` inicia o fluxo; `agents/openai.yaml` contém metadados; `references/` documenta visual, produtos, integrações, qualidade e avaliações; `assets/` contém o tema e interações; `scripts/` gera e testa os sites; `REVISAO.md` registra a entrega e suas limitações.

Código novo e conteúdo de exemplo foram criados para este pacote. Imagens, artigos completos, credenciais, anúncios e contatos dos projetos originais não são redistribuídos. Não foi atribuída uma licença de código aberto sem decisão do proprietário. Consulte a proveniência em `references/visual.md`.

Se ocorrer falha durante a escrita, o gerador desfaz apenas a pasta criada pela própria chamada, desde que sua identidade permaneça a mesma. Ele não apaga pastas preexistentes.
