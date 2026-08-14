# Convite de Formatura — Gabriella

Site de convite interativo (uma página só, sem servidor, sem dependências).

## O que tem dentro

```
site/
├── index.html   ← o convite inteiro (HTML + CSS + JS num arquivo só)
└── img/         ← as fotos (foto-1.jpg … foto-7.jpg)
```

## Como editar

Abra o `index.html` em qualquer editor de texto (até o Bloco de Notas serve).
Logo no começo do arquivo tem um bloco marcado assim:

```
⬇⬇⬇  EDITE SOMENTE ESTE BLOCO  ⬇⬇⬇
```

Ali dentro estão **todos** os textos, datas, locais e a lista de fotos.
Troque só o que está entre aspas e salve. Não precisa mexer em mais nada.

Datas seguem o formato `"ANO-MÊS-DIA HORA:MIN"` — ex.: `"2027-02-19 18:00"`.

### Trocar as fotos

Coloque os arquivos dentro de `img/` e liste os nomes no bloco de configuração:

```js
fotoCapa  : "img/foto-1.jpg",     // foto grande da abertura
fotoFaixa : "img/foto-4.jpg",     // foto atrás da frase
galeria   : ["img/foto-2.jpg", "img/foto-3.jpg", ...]
```

## Como publicar no GitHub Pages

1. Crie uma conta em <https://github.com> (se ainda não tiver).
2. Clique em **New repository**, dê o nome `convite-gabi`, marque **Public** e crie.
3. Na tela do repositório, clique em **uploading an existing file**.
4. Arraste o `index.html` **e a pasta `img` inteira** para a área de upload.
   (Se o navegador não aceitar a pasta, entre em `img`, selecione as 7 fotos e
   arraste — o GitHub mantém a estrutura se você digitar `img/` antes do nome.)
5. Clique em **Commit changes**.
6. Vá em **Settings → Pages**.
7. Em *Source*, escolha **Deploy from a branch**; em *Branch* escolha `main` e `/ (root)`.
   Clique em **Save**.
8. Espere 1–2 minutos e recarregue a página. O endereço aparece lá em cima, no formato:

```
https://SEU-USUARIO.github.io/convite-gabi/
```

Esse é o link para mandar no WhatsApp.

### Miniatura no WhatsApp

Depois que o site estiver no ar, abra o `index.html` e troque a linha:

```html
<meta property="og:image" content="img/foto-1.jpg" />
```

por (com o seu endereço real):

```html
<meta property="og:image" content="https://SEU-USUARIO.github.io/convite-gabi/img/foto-1.jpg" />
```

Assim o link mandado no WhatsApp aparece com a foto dela.

### Dica de peso

As fotos estão com o tamanho original do WhatsApp (~100 KB cada), então o site
abre rápido até no 4G. Se trocar por fotos de câmera profissional, reduza para
no máximo ~1200 px de largura antes de subir.

## A música

O arquivo `musica.mp3` (na mesma pasta do `index.html`) é o que toca de fundo.
Para trocar, é só substituir o arquivo mantendo o mesmo nome — ou apontar outro
nome no bloco de configuração:

```js
musica : "musica.mp3",   // ou true (piano gerado no navegador) ou false (sem música)
volume : 0.55,           // de 0 a 1
```

A música começa quando o convidado abre o envelope (é o toque dele que libera o
áudio nos navegadores) e tem botão de pausa no canto da tela.

Atenção: num repositório público do GitHub o arquivo fica acessível a qualquer
pessoa. Como é uma música comercial, vale saber disso antes de publicar — se
preferir evitar, troque `musica: "musica.mp3"` por `musica: true` e o site usa a
trilha de piano gerada na hora.

## Detalhes técnicos

- Nenhuma biblioteca externa (só as fontes do Google Fonts).
- A trilha de piano é **gerada no navegador** com Web Audio API — não existe
  arquivo de música e não há questão de direitos autorais.
- Respeita `prefers-reduced-motion` (quem tem sensibilidade a movimento vê o
  site sem animações).
- Funciona offline: dá pra abrir o `index.html` direto com dois cliques.
