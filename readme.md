# Jogo do Imperador
## Passo a Passo do Desenvolvimento

### Passo 1
- Crie um arquivo chamado index.html
- Copie o código abaixo e cole neste documento

Documento HTML BASE do Jogo

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Berkshire+Swash&display=swap" rel="stylesheet">
  <link href="estilo.css" rel="stylesheet"> 
  <title>Jogo do Imperador</title>
</head>
<body>
  <h1>Jogo do Imperador</h1>
   

  <main id="game">
      <div class="box">0</div>
      <div class="box">1</div>
      <div class="box">2</div>
      <div class="box">3</div>
      <div class="box">4</div>
      <div class="box">5</div>
      <div class="box">6</div>
      <div class="box">7</div>
      <div class="box">8</div>
      <div class="box">9</div>
    

      <div class="box">10</div>
      <div class="box">11</div>
      <div class="box">12</div>
      <div class="box">13</div>
      <div class="box">14</div>
      <div class="box">15</div>
      <div class="box">16</div>
      <div class="box">17</div>
      <div class="box">18</div>
      <div class="box">19</div>

      <div class="box">20</div>
      <div class="box">21</div>
      <div class="box" >22</div>
      <div class="box">23</div>
      <div class="box">24</div>
      <div class="box">25</div>
      <div class="box">26</div>
      <div class="box">27</div>
      <div class="box">28</div>
      <div class="box">29</div>

      <div class="box">30</div>
      <div class="box">31</div>
      <div class="box">32</div>
      <div class="box">33</div>
      <div class="box">34</div>
      <div class="box">35</div>
      <div class="box">36</div>
      <div class="box">37</div>
      <div class="box">38</div>
      <div class="box">39</div>
      <div class="box">40</div>
      
      <div class="terra1"></div>
      <div class="rio"></div>
      <div class="terra2"></div>

  </main>
  
</body>
</html>


```
## Iniciando o CSS do jogo
- Crie um arquivo com o nome estilo.css e salve na mesma pasta do jogo
- Baixe o [pacote de imagens do jogo](https://github.com/thiagomiranda84/jogodoimperador/raw/main/imagens.zip) e extraia para uma pasta chamada imagens dentro da pasta principal do jogo
- Copie e cole o código abaixo para iniciar o css do Jogo

```css
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}
body{
  background-color:gray;
  height:100vh;
}
h1{
  font-family: 'Berkshire Swash', cursive;
  font-size:5rem;
  color:#FFD700;
  text-shadow:-3px 8px 0px rgb(113, 96, 2),-5px 10px 0px rgb(62, 53, 1), -5px 10px 5px rgba(0,0,0,.5) ;
}
#game{
  width:640px; 
  height:448px; 
  border:1px solid black;
  background-color:white;
  box-shadow:-25px 25px 20px rgba(0,0,0,.5);
  position:relative;
}
.box{
  background-color:#8DAF27;
  border:1px solid #5B7D00;
  width:64px;
  height:64px;
 } 
.terra1{
  background-color:#845635; 
  box-shadow:inset 0px -10px 0px #71492d;
}
.terra2{
  background-color:#845635; 
  box-shadow:inset 0px -5px 2px #71492d;
}
.rio{
  background-color:#6296D0; 
  box-shadow:inset 0 -10px 10px #30649E;
}

```
## Estilizando e Posicionando o Tabuleiro
Adicione as seguintes propriedades no Seletor #game
```css
#game{
  display:grid;
  grid-template-columns: repeat(10,1fr);
  grid-template-rows: repeat(7,1fr);
}
```
### Posicionando os elementos no Tabuleiro
Adicione as seguintes regras nos seletores abaixo
```css
.terra1{
  grid-column:2/span 7;
  grid-row:3/span 1;
 }
.terra2{
  grid-column:2/span 8;
  grid-row:6/span 1;
}
.rio{
  background-color:#6296D0; 
  box-shadow:inset 0 -10px 10px #30649E;
}
```
### Criando o Personagem do Mensageiro e do Rei
Adicione as divs abaixo com o ID game
```html
 <main id="game">
     <div id="mensageiro"></div>
     <div id="imperador"></div>
 </main>    
```
```css
#mensageiro{
  width:32px;
  height:35px;
  background-image:url('imagens/personagem.png');
  background-repeat: no-repeat;
  background-position-x: 0;  
}

#imperador{
  width:25px;
  height:40px;
  background-image:url('imagens/imperador.png');
  background-repeat: no-repeat;
  background-size:contain;
 }

```
## Posicionando o Mensageiro e o Imperador no tabuleiro
Adicione as propriedades abaixo aos seletores relacionados
```css
#mensageiro{
  position:absolute;
  top:0px;
  left:0px;
  z-index: 999;
}
#imperador{
  position:absolute;
  top:256px;
  left:534px;
  z-index: 999;
}

```
### Criando as classes de Animação e Movimentação do Mensageiro
```css
#mensageiro.descendo{
  background-position-y: 0px;
}

#mensageiro.subindo{
  background-position-y: -72px;
}

#mensageiro.direita{
  background-position-y: -36px;
}

#mensageiro.esquerda{
  background-position-y: -108px;
}

#mensageiro.andando{
  animation: andando 500ms steps(3) infinite;
}
@keyframes andando {
  from {background-position-x:0;}
  to {background-position-x:-136px;}
}

```

### Adicionando o Caminho Final ao tabuleiro
```css
.caminhofinal{
  background-color:#E0BD79;
  border-color:#9f8655;
}
```
Adicione a classe caminhofinal aos seguintes Boxes:
```html
      <div class="box caminhofinal">11</div>
      <div class="box caminhofinal">12</div>
      <div class="box caminhofinal">13</div>
      <div class="box caminhofinal">14</div>
      <div class="box caminhofinal">15</div>
      <div class="box caminhofinal">16</div>
      <div class="box caminhofinal">17</div>
      <div class="box caminhofinal">18</div>
      <div class="box">19</div>

      <div class="box">20</div>
      <div class="box caminhofinal">21</div>
      <div class="boxa" >22</div>
      <div class="box">23</div>
      <div class="box caminhofinal">24</div>
      <div class="box">25</div>
      <div class="box">26</div>
      <div class="box caminhofinal">27</div>
      
```

## Estilizando o tabuleiro para o Efeito Isometrico
Adicione as seguintes propriedades CSS aos seletores abaixo
```css
body{
  display:grid;
  place-items: center;
}
h1{
  position:fixed;
  top:0;
}
#game{
  transform: rotate(-10deg) skew(20deg) translate(0,0);
  margin-top:50px;
}
#mensageiro{
  transform:scale(150%) rotate(0deg) skew(-20deg) translate(0,0) scale(150%);
}

#imperador{
  transform: scale(150%) rotate(10deg) skew(-20deg) translate(0,0) scale(150%);
}



```
### Adicionando o Efeito 3D
```css
#game::before{
  content:'';
  position:absolute;
  top:10px;
  left:-20px;
  height:100%;
  width:20px;
  background-image:linear-gradient(to left ,#5B7D00 50%,#845635 50%) ;
  transform:rotate(0deg) skewY(-45deg);  
}
#game::after{
  content:'';
  position:absolute;
  bottom:-20px;
  left:-10px;
  height:20px;
  width:100%;
  background-image:linear-gradient(to bottom ,#405700 50%,#4B3120 50%) ;
  transform:rotate(0deg) skewX(-45deg);  
}
```

### Adicionando Efeito de Profundidade aos Boxes
```css
.frente, 
.frente2, 
.lateral, 
.lateral2, 
.final{
  position:relative;  
}

.frente::after{
  content:'';
  position:absolute;
  bottom:-5px;
  left:-2px;
  width:106%;
  height:10px;
  background-color:#AE8B47;
  transform:rotate(0deg) skewX(15deg);  
}

.frente2::after{
  content:'';
  position:absolute;
  bottom:-5px;
  left:-2px;
  width:106%;
  height:10px;
  background-color:#5B7D00;
  transform:rotate(0deg) skewX(15deg);
  z-index:2;  
}

.final::after{
  content:'';
  position:absolute;
  bottom:-7px;
  left:-8px;
  width:108%;
  height:10px;
  background-color:#AE8B47;
  transform:rotate(0deg) skewX(-30deg);  
}

.lateral::before{
  content:'';
  position:absolute;
  left:-11px;
  bottom:-3px;
  width:10px;
  height:105%;
  transform:rotate(0deg) skewY(-30deg);
  background-color:#AE8B47;
}
.lateral2::before{
  content:'';
  position:absolute;
  left:-10px;
  bottom:0px;
  width:8px;
  height:105%;
  transform:rotate(0deg) skewY(-30deg);
  background-color:#5B7D00;
}

```
Adicione as classes .frente .frente2,.lateral,.lateral2,.final aos seguintes boxes

```html
      <div class="box frente2">0</div>
      <div class="box frente2">1</div>
      <div class="box frente2">2</div>
      <div class="box frente2">3</div>
      <div class="box frente2">4</div>
      <div class="box frente2">5</div>
      <div class="box frente2">6</div>
      <div class="box frente2">7</div>
      <div class="box frente2">8</div>
      <div class="box">9</div>
    
      <div class="box">10</div>
      <div class="box caminhofinal frente">11</div>
      <div class="box caminhofinal frente">12</div>
      <div class="box caminhofinal frente">13</div>
      <div class="box caminhofinal frente">14</div>
      <div class="box caminhofinal frente">15</div>
      <div class="box caminhofinal frente">16</div>
      <div class="box caminhofinal frente">17</div>
      <div class="box caminhofinal frente">18</div>
      <div class="box lateral2">19</div>

      <div class="box">20</div>
      <div class="box caminhofinal lateral">21</div>
      <div class="box lateral2" >22</div>
      <div class="box">23</div>
      <div class="box caminhofinal lateral">24</div>
      <div class="box lateral2">25</div>
      <div class="box">26</div>
      <div class="box caminhofinal final lateral">27</div>
      <div class="box lateral2 ">28</div>
      <div class="box">29</div>

      <div class="box lateral2">30</div>
      <div class="box">31</div>
      <div class="box">32</div>
      <div class="box">33</div>
      <div class="box">34</div>
      <div class="box ">35</div>
      <div class="box">36</div>
      <div class="box">37</div>
      <div class="box">38</div>
      <div class="box">39</div>
      <div class="box">40</div>

```

### Adicionando as Setas aos Boxes
Adicione as seguintes classes ao documento CSS
```css
.setabaixo{
  background-image:url("imagens/setabaixo.png");
  background-size:100%;
  background-position:center;
  background-repeat:no-repeat;

}

.setaesquerda{
  background-image:url("imagens/setaesquerda.png");
  background-size:100%;
  background-position:center;
  background-repeat:no-repeat;

}

.setacima{
  background-image:url("imagens/setacima.png");
  background-size:100%;
  background-position:center;
  background-repeat:no-repeat;

}

.setadireita{
  background-image:url("imagens/setadireita.png");
  background-size:100%;
  background-position:center;
  background-repeat:no-repeat;

}

.setabaixofinal{
  background-image:url("imagens/setabaixofinal.png");
  background-size:100%;
  background-position:center;
  background-repeat:no-repeat;

}
.setafrente{
  background-image:url("imagens/setafrente.png");
  background-size:100%;
  background-position:center;
  background-repeat:no-repeat;

}

```

Adicione as classes correspondentes aos Boxes abaixo

```html
      <div class="box frente2 setafrente">0</div>
     <div class="box setabaixo">9</div>
     <div class="box setadireita">10</div>
     <div class="box caminhofinal setabaixofinal">18</div>
     <div class="box setacima">31</div>
     <div class="box setaesquerda">40</div>

```

## Criando as Classes de ações dos Boxes
```css
.questao{
  background-image:url("imagens/questao.png");
  background-size:50%;
  background-position:center;
  background-repeat:no-repeat;
}

.surpresa{
  background-image:url("imagens/surpresa.png");
  background-size:50%;
  background-position:center;
  background-repeat:no-repeat;
}

.moeda{
  background-image:url("imagens/moeda.png");
  background-size:55%;
  background-position:center;
  background-repeat:no-repeat;
}
```
Adicione Aleatoriamente esta classe nos Boxes que não contenham as setas.

## Adicionando a classe para mostrar o box atual do personagem
```css
.atual{
  background-color:#add338;
}
.caminhofinal.atual{
  background-color:#ffe4ae;
}
```

## Criando o Dado

```html
<div id="area-dado">
    <h2>Clique no dado para jogar</h2>
    <div id="dado">
      <div class="ponto"></div>
      <div class="ponto"></div>
      <div class="ponto"></div>
    </div>
 </div>

```

```css
#area-dado{
  position:fixed;
  right:2rem;
  top:10vh;
  background-color:#ecf0f1;
  width:300px;
  height: 300px;
  padding:1rem;
  border-radius:20px;
  display: grid;
  place-items: center;
  box-shadow:-5px 5px 10px rgba(0,0,0,.3);
}
#area-dado h2{
  text-align: center;
  font-family: 'Berkshire Swash', cursive;
}

#dado{
  width:160px;
  height:160px;
  border:1px solid #AAA;
  background-color: #e7e7e7;
  box-shadow: inset 0 5px white, inset 0 -5px #bbb, inset 5px 0 #d7d7d7, inset -5px 0 #d7d7d7;
  border-radius: 10%;
  cursor:pointer;
  padding:.2rem;
}

.ponto {
    align-self: center;
    justify-self: center;
    width: 24px;
    height: 24px;
    border-radius: 50%;
    background-color: #333;
    box-shadow: inset 0 3px #111, inset 0 -3px #555;
}


```
#### Posicionando os pontos dentro do dado

```css
.ponto:nth-child(2) {
grid-area: b;
}
.ponto:nth-child(3) {
grid-area: c;
}
.ponto:nth-child(4) {
grid-area: d;
}
.ponto:nth-child(5) {
grid-area: e;
}
.ponto:nth-child(6) {
grid-area: f;
}
.ponto:nth-child(odd):last-child {
grid-area: g;
}

#dado{
  display:grid;
  grid-template-areas:
      "a . c"
      "e g f"
      "d . b";
}
```
### Adicionando uma classe de animação para o dado
```css
.mexer{
  animation:mexer 0.5s infinite;
  border:1px solid blue;
}


@keyframes mexer{
  0%{
      transform:rotate(8deg);
  }
  50%{
      transform: rotate(-8deg);
  }
  100%{
      transform:rotate(8deg);
  }
}
```







