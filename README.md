<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    
    <meta name="referrer" content="always">
    
    <meta name="color-scheme" content="light only">
    <meta name="supported-color-schemes" content="light">
    <title>Casamento - Walter & Arija</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">
    
    <style>
        /* Reset e Otimização para iOS */
        * { 
            -webkit-font-smoothing: antialiased; 
            -moz-osx-font-smoothing: grayscale; 
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        html {
            background-color: #fdfdfd;
            margin: 0; padding: 0; height: 100%;
        }

        body {
            margin: 0; padding: 0;
            font-family: 'Montserrat', sans-serif;
            color: #333333;
            /* NOVOS LINKS DAS FLORES */
            background-image: url('https://i.postimg.cc/QCPLG3NQ/Flor_1.png'), url('https://i.postimg.cc/90S35hXZ/Flor_2.png'); 
            background-position: top left, bottom right;
            background-repeat: no-repeat;
            background-size: 150px;
            background-attachment: scroll;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            background-color: #fdfdfd;
        }

        /* PÉTALAS */
        .petala {
            position: fixed; 
            top: -50px;
            background-color: #005f73; 
            border-radius: 100% 0 100% 0;
            opacity: 0.8; 
            z-index: 5; 
            pointer-events: none;
            animation: cair_e_girar 8s linear infinite;
        }

        @keyframes cair_e_girar {
            0% { top: -50px; transform: translateX(0) rotate(0deg); opacity: 0; }
            15% { opacity: 0.8; }
            100% { top: 100vh; transform: translateX(-50px) rotate(360deg); opacity: 0; }
        }

        .container {
            max-width: 450px;
            margin: 20px auto; 
            padding: 30px 20px;
            background: #ffffff;
            border: 1px solid #e0e0e0;
            border-radius: 20px;
            position: relative;
            z-index: 10; 
            text-align: center;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
        }

        .foto-wrapper { 
            position: relative; 
            width: 100%; 
            margin-bottom: 20px; 
            overflow: hidden;
            border-radius: 15px;
        }

        .imagem-topo { 
            width: 100%; 
            display: block; 
            height: auto; 
            border-radius: 15px;
        }
        
        h1 { 
            font-family: 'Great Vibes', cursive; 
            font-size: 3.5rem; 
            color: #ADD8E6; 
            margin: 25px 0; 
            word-spacing: 35px;
            -webkit-text-fill-color: #ADD8E6;
        }

        .data {
            font-size: 1.1rem; 
            letter-spacing: 2px;
            border-top: 1px solid #ADD8E6;
            border-bottom: 1px solid #ADD8E6;
            padding: 10px 0; 
            margin: 20px 0; 
            display: inline-block;
        }

        .botoes-lado-a-lado {
            display: flex; 
            justify-content: center; 
            gap: 15px; 
            margin: 25px 0;
        }

        .item-botao {
            display: flex; 
            flex-direction: column; 
            align-items: center;
            width: 100px; 
            text-decoration: none; 
            cursor: pointer; 
            background: none; 
            border: none;
            padding: 0;
        }

        .item-botao img { 
            width: 80px; 
            height: auto; 
            margin-bottom: 8px; 
            display: block;
        }

        .legenda {
            font-size: 0.65rem; 
            color: #555555;
            font-weight: bold; 
            text-transform: uppercase; 
            letter-spacing: 1px;
        }

        /* MODAL PIX */
        .modal {
            display: none; 
            position: fixed; 
            z-index: 1000;
            left: 0; top: 0; 
            width: 100%; height: 100%;
            background-color: rgba(0,0,0,0.6);
            -webkit-backdrop-filter: blur(5px);
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background-color: #ffffff;
            margin: 10vh auto; 
            padding: 25px;
            border-radius: 20px; 
            width: 85%; 
            max-width: 380px;
            text-align: center; 
            position: relative;
            max-height: 85vh; 
            overflow-y: auto;
        }

        .qr-code-pix {
            width: 180px; 
            height: auto;
            margin: 15px auto; 
            border: 1px solid #eee;
            padding: 10px; 
            border-radius: 10px;
            display: block;
        }

        .fechar-modal {
            position: absolute; 
            right: 15px; 
            top: 10px;
            font-size: 28px; 
            cursor: pointer; 
            color: #999;
        }

        @media (max-width: 600px) {
            .container { margin: 15px; }
            h1 { font-size: 2.8rem; word-spacing: 20px; }
            .item-botao img { width: 65px; }
            body { background-size: 100px; }
        }
    </style>
</head>
<body>

<script>
    function criarPetala() {
        const petala = document.createElement('div');
        petala.className = 'petala';
        petala.style.left = Math.random() * 100 + 'vw';
        const tamanho = Math.random() * 15 + 10 + 'px';
        petala.style.width = tamanho; 
        petala.style.height = tamanho;
        const duracao = Math.random() * 5 + 5 + 's';
        petala.style.animationDuration = duracao;
        document.body.appendChild(petala);
        setTimeout(() => { petala.remove(); }, 8000);
    }
    
    setInterval(criarPetala, 500);

    function abrirModal() { document.getElementById("modalPix").style.display = "block"; }
    function fecharModal() { document.getElementById("modalPix").style.display = "none"; }
    
    window.onclick = function(event) {
        let modal = document.getElementById("modalPix");
        if (event.target == modal) { modal.style.display = "none"; }
    }
</script>

<div class="container">
    <div class="foto-wrapper">
        <img src="https://i.postimg.cc/cCjqyS1f/Pictures_1.png" alt="Walter e Arija" class="imagem-topo">
    </div>
    
    <h1>Walter & Arija</h1>

    <p>Vamos nos casar no civil, e gostaríamos de convidar você para celebrar em um almoço.</p>

    <div class="data">25 | JANEIRO | 2026</div>

    <div class="detalhes">
        <p><strong>Horário:</strong> 10:30h</p>
        <p><strong>Local:</strong> Chácara Pedacinho do Céu</p>
        <p>MS 384 - Km 04</p>
    </div>

    <hr style="border: 0; border-top: 1px solid #eee; margin: 25px 0;">

    <div class="botoes-lado-a-lado">
        <a href="https://wa.me/556793251334" target="_blank" class="item-botao">
            <img src="https://i.postimg.cc/4yMCkg49/Whatsapp_btn.png" alt="WhatsApp">
            <span class="legenda">Confirmar Presença</span>
        </a>

        <button onclick="abrirModal()" class="item-botao">
            <img src="https://i.postimg.cc/d3DMx1F6/Lista_de_Presentes.png" alt="Presentes">
            <span class="legenda">Sugestão de Presentes</span>
        </button>

        <a href="https://www.google.com/maps/search/?api=1&query=MS+384+Km+04+Chácara+Pedacinho+do+Céu" target="_blank" class="item-botao">
            <img src="https://i.postimg.cc/SR50FhQz/Mapa_btn.png" alt="Mapa">
            <span class="legenda">Como Chegar</span>
        </a>
    </div>

    <p style="font-size: 0.7rem; margin-top: 30px; opacity: 0.5;">#CasamentoWalterArija2026</p>
</div>

<div id="modalPix" class="modal">
    <div class="modal-content">
        <span class="fechar-modal" onclick="fecharModal()">×</span>
        <h2 style="font-family: 'Great Vibes'; color: #ADD8E6; font-size: 2.2rem; margin-bottom: 10px;">Sugestões de presentes</h2>
        
        <p style="font-size: 0.85rem; line-height: 1.5; color: #555; margin-bottom: 10px;">
            Dividir esses momentos com vocês é o que mais desejamos. Não fizemos lista de presentes, mas caso queira nos agraciar com algum presente sugerimos uma contribuição através do PIX.
        </p>

        <img src="https://i.postimg.cc/BbtWV63g/Pix.png" alt="QR Code Pix" class="qr-code-pix">
        
        <div style="background: #f9f9f9; padding: 12px; border-radius: 10px; border: 1px dashed #ADD8E6;">
            <p style="font-weight: bold; margin-bottom: 5px; font-size: 0.75rem; color: #888;">CHAVE PIX (E-MAIL):</p>
            <p style="color: #005f73; font-weight: bold; font-size: 0.95rem; word-break: break-all;">waltergabrielmaster@gmail.com</p>
        </div>

        <button onclick="fecharModal()" style="margin-top: 20px; background: #ADD8E6; color: white; border: none; padding: 10px 25px; border-radius: 20px; font-family: 'Montserrat'; font-weight: bold; cursor: pointer; width: 100%;">
            VOLTAR AO CONVITE
        </button>
    </div>
</div>

</body>
</html>
