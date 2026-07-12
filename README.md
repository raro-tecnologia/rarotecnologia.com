# Raro Tecnologia — site institucional

Site estático (HTML/CSS/JS, sem build) da **Raro Tecnologia**, com foco em **Automação e IA** e **Consultoria em IA**. Hospedado no GitHub Pages em [rarotecnologia.com](https://rarotecnologia.com).

## Stack

- HTML + CSS puro (custom properties, sem framework)
- JavaScript vanilla para i18n (PT/EN) via `data-i18n` + `localStorage`
- Fontes: Inter (display) e IBM Plex Sans (corpo), via Google Fonts
- Deploy: GitHub Pages (branch `main`, raiz `/`) + domínio custom (`CNAME`)

## Estrutura

```
.
├── index.html          # página principal (hero, métricas, serviços, sobre, contato)
├── terms.html          # termos de serviço
├── privacy.html        # política de privacidade
├── i18n.js             # traduções PT/EN (chaves data-i18n) e troca de idioma
├── styles.css          # agregador: só @import dos módulos abaixo (ordem = cascata)
├── css/
│   ├── base.css        # reset, tokens (:root), tipografia, botões, section-tag
│   ├── layout.css      # header, nav, logo lockup, seletor de idioma, hero
│   ├── sections.css    # métricas, serviços, sobre, contato, footer, páginas legais
│   ├── responsive.css  # breakpoints (1024 / 768 / 480)
│   └── enhancements.css # CTAs, botões WhatsApp, cena de chat, ajustes finos
├── logo/               # símbolo (transparente/branco) em PNG e WebP (256/512/1024)
├── favicon/            # favicon.ico + PNG/WebP + apple-touch-icon
├── og-image.jpeg/.webp # imagem de compartilhamento social (1200×630)
├── robots.txt
└── CNAME               # domínio custom (rarotecnologia.com)
```

## Rodar localmente

Como é estático, basta um servidor HTTP simples na raiz do projeto:

```bash
python3 -m http.server 8000
# abrir http://localhost:8000
```

## Editar conteúdo

- **Textos:** cada texto traduzível tem um atributo `data-i18n="chave"`. Adicione/edite a chave nos dois idiomas em `i18n.js` (`pt` e `en`). Todo texto novo precisa existir nas duas línguas.
- **Estilos:** edite o módulo correspondente em `css/`. A ordem dos `@import` em `styles.css` define a cascata — mantenha-a.
- **Cache-busting:** ao alterar CSS ou JS, suba a versão `?v=N` no `@import` (para CSS) **e** nas tags `<link>`/`<script>` de `index.html`, `terms.html` e `privacy.html`.
- **Nova página:** copie o bloco `<head>` do `index.html` (favicon + **Google Fonts** + `styles.css?v=N`) para garantir tipografia e logo idênticos.

## Contato / marca

- WhatsApp: +55 44 93618-0471 · Instagram: [@raro_tecnologia](https://instagram.com/raro_tecnologia) · E-mail: contato@rarotecnologia.com
- Uso da marca: **"Raro Tecnologia"** em texto/prosa; **"RARO"** apenas como marca/logo.

## Deploy

Push na branch `main` publica automaticamente via GitHub Pages.

```bash
git add -A
git commit -m "descrição da mudança"
git push
```

DNS (Cloudflare, "Somente DNS"): registros **A** do apex apontando para os IPs do GitHub Pages (`185.199.108–111.153`) e **CNAME** `www` → `raro-tecnologia.github.io`.
