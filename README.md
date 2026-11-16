# QI do Chat

Quiz interativo para lives da Twitch: o chat responde digitando **A**, **B**, **C** ou **D**, um apresentador zoa todo mundo e os pontos valem ranking do dia, do mês e geral.

**Um quadro criado por [PlayerNubya](https://twitch.tv/playernubya).**

Abra o link, digite o nome do seu canal e pronto. Não precisa criar conta, instalar nada nem cadastrar aplicativo.

---

## Como usar (3 passos)

1. **Abra o link do jogo** no navegador do computador e digite o nome do seu canal na Twitch.
2. **Copie o endereço** que aparece e cole no OBS: fonte do tipo **Navegador**, largura **1920**, altura **1080**, com **Controlar áudio via OBS** marcado.
3. **No chat**, digite `!qi` para começar. Quem assiste responde com **A**, **B**, **C** ou **D**.

Para testar antes da live, clique em **ver uma demonstração**: um chat falso joga sozinho.

### Comandos

| Comando | O que faz |
|---|---|
| `!qi` | começa uma rodada (ou continua depois da pausa) |
| `!qi games` | escolhe o tema (lista abaixo) |
| `!qi pausa` / `!qi pular` | pausa depois da pergunta atual / pula a atual |
| `!qi relampago` | próxima pergunta vale o dobro |
| `!qi ranking` | mostra o ranking |
| `!qi fim` | encerra a rodada |
| `!qi abrir` / `!qi fechar` | mostra ou esconde a janela |
| `!qi som` / `!qi trilha` | desliga todos os sons / só a música |
| `!qi fotos` / `!qi mascote` | liga e desliga a arquibancada / o apresentador |
| `!qi novalive` | começa um ranking "Hoje" novo |
| `!qi zerar hoje\|mes\|tudo` | zera o ranking escolhido (só o dono do canal) |

Quem assiste consulta a própria posição com **!pontos**.

**Temas:** games, filmes, series, musica, brasil, historia, literatura, geek, ciencia, curiosidades, esportes, tv, memes, infancia, mitologia, geografia, leis, mix.
**Subtemas:** dbd, cs, re, sh, tlou, minecraft, pokemon, nintendo, zelda, gta, lol, amongus, classicos, terror, marvel, disney, hp, starwars, nacional, sucessos, st, friends, got, animes, variadas, anos80, brasileira, rock, kpop.

---

## Painel de controle

Para jogar por botões e **editar perguntas e falas durante a live**, abra o mesmo endereço com `?painel` no fim, ou o arquivo `painel.html`.

No OBS: adicione uma **segunda fonte de navegador** com esse endereço, deixe oculta ou fora da tela e use clicando com o botão direito em **Interagir**.

O painel faz:

- **Controles**: iniciar, pausar, pular, relâmpago, ranking, encerrar, trocar de tema
- **Perguntas**: buscar entre as 1.929, corrigir, desativar e criar as suas
- **Falas do apresentador**: desativar as que não combinam com o seu chat e adicionar as piadas internas do canal
- **Backup**: salvar e restaurar rankings, perguntas e configurações
- **Configurações**: tempos, sons, volume, lado da janela, pontuação, premiação

> Edições ficam guardadas no navegador onde você mexeu. O que você editar no Chrome **não** aparece no OBS. Para valer na live, use o painel dentro do OBS.

### Backup (não pule)

O ranking fica salvo dentro da fonte de navegador do OBS. Se o OBS limpar o cache, some tudo. No painel, em **BACKUP**, clique em **Gerar backup na caixa**, copie o texto e guarde num arquivo seu. Para restaurar, cole e clique em **Importar**.

---

## Recursos opcionais

### Premiar com pontos do canal (StreamElements)

No painel, cartão **NUBYACOINS**: pegue o **JWT Token** em streamelements.com → avatar → **Account** → **Show secrets**, cole no campo, clique em **Testar conexão** e salve. Escolha se premia só o campeão, o top 3 ou todo mundo.

> O token dá controle da sua conta do StreamElements. Não mostre o painel na live.

### Mascote

O arquivo `mascote.gif` é o apresentador. Para usar outro, troque o arquivo mantendo o nome. Expressões opcionais: `mascote-feliz.gif`, `mascote-triste.gif`, `mascote-chocado.gif`, `mascote-dormindo.gif`. Sem elas, o jogo reage com animações em cima do mascote padrão.

### Pontuação

No painel: **peso da velocidade** (0% = todo acerto vale igual, bom para quem tem muito delay), **janela de velocidade** e **penalidade por erro** (desestimula o chute). A velocidade é contada a partir do primeiro acerto, não da abertura da pergunta, justamente para o delay da Twitch não decidir quem ganha.

### Login com a Twitch (avançado)

Só vale a pena para liberar o **!pontos respondendo no próprio chat**. Exige registrar um aplicativo em [dev.twitch.tv/console/apps](https://dev.twitch.tv/console/apps) com a URL de redirecionamento `https://SEU-ENDERECO/painel.html`, e colar o Client ID na linha `const CLIENT_ID` no começo do `index.html`. Sem isso, o painel mostra só o campo de canal, que é o suficiente.

---

## Como colocar no ar

O jogo é um site estático: três arquivos e nenhum servidor. Duas formas fáceis:

### Opção 1 — Netlify Drop (2 minutos, sem conta)

1. Descompacte o zip numa pasta
2. Entre em [app.netlify.com/drop](https://app.netlify.com/drop)
3. Arraste a **pasta inteira** para a área indicada
4. Em segundos você recebe um endereço tipo `https://algo-aleatorio.netlify.app` — é esse que você compartilha

Crie uma conta gratuita depois se quiser escolher um nome melhor (`qidochat.netlify.app`) e manter o site para sempre.

### Opção 2 — GitHub Pages

1. Crie um repositório público chamado `qi-do-chat`
2. Envie todos os arquivos desta pasta para a raiz dele
3. Em **Settings → Pages**, em *Source* escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`
4. Em um ou dois minutos o jogo estará em `https://SEU-USUARIO.github.io/qi-do-chat/`

### Opção 3 — sem internet

Também funciona abrindo o `index.html` direto do computador, sem hospedar. Só não dá para mandar o link para ninguém.

---

## Perguntas frequentes

**Preciso de bot ou de servidor?** Não. O jogo lê o chat sozinho, direto do navegador.

**Funciona em canal pequeno?** Funciona. Com duas pessoas no chat já roda.

**As perguntas se repetem?** Não, até acabarem as do tema. Aí o jogo embaralha de novo.

**Dá para pular a tela inicial?** Sim: acrescente `?canal=seunome` no fim do endereço.

**As fotos do chat não aparecem.** Elas vêm de um serviço externo gratuito. Se ele estiver fora do ar, o jogo desenha avatares coloridos com a inicial de cada um.

---

## Créditos

Criado por **PlayerNubya** ([Twitch](https://twitch.tv/playernubya) · [TikTok](https://tiktok.com/@playernubya) · [Instagram](https://instagram.com/playernubya) · [YouTube](https://youtube.com/@playernubya)).

Se usar na sua live, deixe o crédito na tela e manda um alô. 💜
