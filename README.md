# Extrator de Infrações

Ferramenta HTML single-file que extrai as imagens base64 dos JSON de infração e analisa os tempos de captura. Roda 100% local no navegador — nenhum dado sai da máquina.

## Uso

Abra `index.html` no Chrome/Edge e:

- **Abrir pasta…** — lê a pasta (ex.: `20261006`) com permissão de gravação; permite salvar as imagens ao lado dos JSON
- **Modo compatível / arquivos JSON / arrastar e soltar** — leitura sem gravação (saída via ZIP)

## Saídas

- **Salvar imagens na pasta** — grava `<json>_<n>_<role>_<source>.jpg` junto de cada JSON (Chrome/Edge)
- **Baixar ZIP** — todas as imagens + `tempos_captura.csv` (sem compressão)
- **Baixar CSV de tempos** — separador `;`, UTF-8 com BOM (abre direto no Excel)

## Análise

- KPIs: mediana/mín/máx de `elapsedMs` da CGI, L2 → eventAt, eventAt → fim do Evento CGI, L1 → fim do Evento CGI
- Linha do tempo por evento (ms relativos à entrada no laço 1; sem laço, relativos ao `eventAt`), com barras de requisição por imagem
- Validação de `sizeBytes` contra o tamanho real decodificado
- Visualizador de imagens com metadados (Esc fecha)
