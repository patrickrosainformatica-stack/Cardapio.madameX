<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>Madame X Pub - Cardápio Digital</title>
    <style>
        :root {
            --primary-color: #1a1a2e;
            --secondary-color: #e94560;
            --accent-color: #ff9a3c;
            --gold-color: #ffd166;
            --dark-color: #0f3460;
            --light-color: #f0f0f0;
            --text-color: #333;
            --shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
            --radius: 12px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Roboto', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0f0c29 0%, #302b63 50%, #24243e 100%);
            color: var(--light-color);
            line-height: 1.6;
            min-height: 100vh;
            padding-top: 140px;
            -webkit-tap-highlight-color: transparent;
            overflow-x: hidden;
        }

        /* Tela de abertura */
        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #0f0c29 0%, #302b63 50%, #24243e 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.8s ease, visibility 0.8s ease;
            padding: 20px;
            text-align: center;
        }

        .splash-screen.hidden {
            opacity: 0;
            visibility: hidden;
            pointer-events: none;
        }

        .splash-logo {
            max-width: 300px;
            width: 90%;
            height: auto;
            filter: drop-shadow(0 10px 25px rgba(255, 209, 102, 0.5));
            animation: float 6s ease-in-out infinite;
            margin-bottom: 2rem;
        }

        .splash-title {
            font-size: 2.5rem;
            background: linear-gradient(45deg, var(--gold-color), #ff9a3c);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 1px;
            text-shadow: 0 2px 10px rgba(255, 209, 102, 0.3);
            margin-bottom: 1rem;
        }

        .splash-subtitle {
            color: var(--gold-color);
            font-size: 1.2rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .enter-button {
            background: linear-gradient(135deg, var(--secondary-color), #c1121f);
            color: white;
            border: none;
            padding: 1rem 2.5rem;
            border-radius: 30px;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(233, 69, 96, 0.4);
            margin-top: 1rem;
        }

        .enter-button:hover,
        .enter-button:active {
            transform: scale(1.05);
            box-shadow: 0 6px 20px rgba(233, 69, 96, 0.6);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header com logo maior */
        header {
            background: linear-gradient(rgba(26, 26, 46, 0.98), rgba(26, 26, 46, 0.98));
            padding: 1rem 0;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
            border-bottom: 3px solid var(--gold-color);
            backdrop-filter: blur(10px);
        }

        .header-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.8rem;
        }

        .logo-section {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .pub-logo {
            height: 120px;
            width: auto;
            filter: drop-shadow(0 2px 8px rgba(255, 209, 102, 0.4));
            animation: pulse 3s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .header-text {
            text-align: center;
        }

        h1 {
            font-size: 2.2rem;
            background: linear-gradient(45deg, var(--gold-color), #ff9a3c);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 0.8px;
            text-shadow: 0 2px 10px rgba(255, 209, 102, 0.3);
        }

        .subtitle {
            font-size: 1rem;
            color: var(--gold-color);
            font-weight: 300;
            letter-spacing: 1.5px;
        }

        /* Menu de navegação */
        .nav-wrapper {
            background: rgba(15, 52, 96, 0.98);
            position: fixed;
            top: 150px;
            left: 0;
            right: 0;
            z-index: 999;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            backdrop-filter: blur(10px);
            border-bottom: 2px solid rgba(255, 209, 102, 0.3);
        }

        .nav-container {
            overflow-x: auto;
            padding: 0.3rem 0;
            -webkit-overflow-scrolling: touch;
            scrollbar-width: none;
            -ms-overflow-style: none;
        }

        .nav-container::-webkit-scrollbar {
            display: none;
        }

        nav {
            display: flex;
            padding: 0.3rem 0;
            min-width: max-content;
            gap: 0.3rem;
            padding: 0 15px;
        }

        .nav-btn {
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid transparent;
            color: white;
            padding: 0.6rem 1.2rem;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.2s ease;
            font-weight: 600;
            font-size: 0.8rem;
            white-space: nowrap;
            flex-shrink: 0;
            min-height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }

        .nav-btn:hover,
        .nav-btn:active {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-1px);
            border-color: rgba(255, 209, 102, 0.5);
        }

        .nav-btn.active {
            background: linear-gradient(135deg, var(--secondary-color), #c1121f);
            color: white;
            border-color: var(--secondary-color);
            box-shadow: 0 2px 8px rgba(233, 69, 96, 0.4);
        }

        /* Seção de arte e boas-vindas ATUALIZADA */
        .art-section {
            padding: 2rem 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .art-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;
        }

        .main-art {
            max-width: 280px;
            width: 100%;
            height: auto;
            filter: drop-shadow(0 5px 15px rgba(255, 154, 60, 0.3));
            animation: float 6s ease-in-out infinite;
            border-radius: 15px;
            margin: 0 auto;
        }

        .welcome-art {
            max-width: 250px;
            width: 100%;
            height: auto;
            filter: drop-shadow(0 5px 15px rgba(255, 209, 102, 0.3));
            border-radius: 15px;
            margin: 0 auto;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .welcome-text {
            max-width: 600px;
            padding: 1.5rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 209, 102, 0.2);
        }

        .welcome-text h2 {
            font-size: 1.8rem;
            color: var(--gold-color);
            margin-bottom: 1rem;
            text-shadow: 0 2px 5px rgba(0,0,0,0.5);
        }

        .welcome-text p {
            font-size: 1rem;
            line-height: 1.6;
            color: #e0e0e0;
        }

        /* Conteúdo Principal */
        main {
            padding: 1.5rem 0 3rem;
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .category {
            display: none;
            margin-bottom: 2.5rem;
        }

        .category.active {
            display: block;
            animation: slideUp 0.3s ease;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .category-header {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            margin-bottom: 1.5rem;
            padding-bottom: 0.8rem;
            border-bottom: 2px solid var(--accent-color);
        }

        .category-icon {
            font-size: 2rem;
        }

        .category-title {
            font-size: 1.8rem;
            color: var(--gold-color);
            margin: 0;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        /* Items Grid - Otimizado para mobile */
        .items-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1rem;
            margin-top: 1rem;
        }

        .item-card {
            background: linear-gradient(145deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
            border-radius: var(--radius);
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }

        .item-card:active {
            transform: scale(0.98);
            border-color: var(--accent-color);
        }

        .item-content {
            padding: 1.2rem;
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            flex-direction: column;
            gap: 0.8rem;
        }

        .item-info {
            width: 100%;
        }

        .item-name {
            font-size: 1.1rem;
            font-weight: 700;
            color: var(--gold-color);
            margin-bottom: 0.4rem;
            display: flex;
            align-items: center;
            gap: 6px;
            line-height: 1.3;
        }

        .item-name::before {
            content: '✦';
            color: var(--accent-color);
            font-size: 1rem;
        }

        .item-description {
            font-size: 0.85rem;
            color: #b0b0b0;
            line-height: 1.5;
            margin-bottom: 0.5rem;
        }

        .item-price {
            font-size: 1.4rem;
            font-weight: 800;
            color: white;
            background: linear-gradient(45deg, var(--secondary-color), #c1121f);
            padding: 0.6rem 1.2rem;
            border-radius: 25px;
            border: 2px solid rgba(255, 255, 255, 0.2);
            text-align: center;
            align-self: flex-end;
            box-shadow: 0 2px 8px rgba(233, 69, 96, 0.3);
            min-width: 100px;
        }

        /* Subcategories */
        .subcategory {
            margin-bottom: 2rem;
            padding: 1.2rem;
            background: rgba(0, 0, 0, 0.2);
            border-radius: var(--radius);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .subcategory-title {
            font-size: 1.4rem;
            color: var(--accent-color);
            margin-bottom: 1rem;
            padding-left: 10px;
            border-left: 3px solid var(--accent-color);
        }

        /* Special Items */
        .combo-item {
            background: linear-gradient(135deg, rgba(15, 52, 96, 0.6), rgba(26, 26, 46, 0.6));
            border: 2px solid var(--gold-color);
        }

        .combo-details {
            margin-top: 1rem;
            padding-top: 1rem;
            border-top: 1px solid rgba(255, 209, 102, 0.3);
        }

        .combo-items {
            display: grid;
            grid-template-columns: 1fr;
            gap: 6px;
            margin-top: 0.8rem;
        }

        .combo-item-name {
            background: rgba(255, 255, 255, 0.1);
            padding: 8px 12px;
            border-radius: 6px;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .combo-item-name::before {
            content: '★';
            color: var(--accent-color);
            font-size: 0.9rem;
        }

        /* Footer atualizado */
        footer {
            background: linear-gradient(rgba(26, 26, 46, 0.95), rgba(15, 52, 96, 0.95));
            text-align: center;
            padding: 2rem 0;
            margin-top: 2rem;
            border-top: 2px solid var(--gold-color);
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1.5rem;
        }

        .footer-logos {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            gap: 2rem;
            margin-bottom: 1.5rem;
        }

        .footer-logo {
            height: 80px;
            width: auto;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3));
            transition: transform 0.3s ease;
        }

        .footer-logo:hover {
            transform: scale(1.05);
        }

        .pixel-frame-logo {
            height: 70px;
        }

        .footer-info {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            font-size: 0.95rem;
            color: var(--gold-color);
            padding: 0.5rem 1rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 25px;
            backdrop-filter: blur(5px);
        }

        .copyright {
            margin-top: 1rem;
            font-size: 0.8rem;
            color: #888;
            line-height: 1.4;
        }

        /* Botão de scroll para mobile */
        .scroll-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: linear-gradient(135deg, var(--secondary-color), #c1121f);
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            display: none;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            box-shadow: 0 4px 15px rgba(233, 69, 96, 0.4);
            z-index: 1000;
            transition: transform 0.2s;
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }

        .scroll-top:active {
            transform: scale(0.95);
        }

        /* Mobile First - Ajustes específicos para smartphone */
        @media (max-width: 767px) {
            body {
                padding-top: 130px;
            }
            
            .pub-logo {
                height: 100px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .subtitle {
                font-size: 0.9rem;
            }
            
            .nav-wrapper {
                top: 130px;
            }
            
            .nav-btn {
                padding: 0.5rem 1rem;
                font-size: 0.75rem;
                min-height: 32px;
            }
            
            .splash-logo {
                max-width: 250px;
            }
            
            .splash-title {
                font-size: 2rem;
            }
            
            .main-art {
                max-width: 220px;
            }
            
            .welcome-art {
                max-width: 200px;
            }
            
            .welcome-text {
                padding: 1.2rem;
                margin: 0 10px;
            }
            
            .welcome-text h2 {
                font-size: 1.5rem;
            }
            
            .welcome-text p {
                font-size: 0.9rem;
            }
            
            .item-content {
                padding: 1rem;
            }
            
            .item-price {
                font-size: 1.2rem;
                padding: 0.5rem 1rem;
                min-width: 90px;
            }
            
            .footer-logo {
                height: 60px;
            }
            
            .pixel-frame-logo {
                height: 55px;
            }
        }

        /* Tablet */
        @media (min-width: 768px) and (max-width: 1023px) {
            body {
                padding-top: 180px;
            }
            
            .pub-logo {
                height: 130px;
            }
            
            .nav-wrapper {
                top: 160px;
            }
            
            .splash-logo {
                max-width: 350px;
            }
            
            .main-art {
                max-width: 320px;
            }
            
            .welcome-art {
                max-width: 280px;
            }
            
            .items-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .item-content {
                flex-direction: row;
                align-items: center;
            }
            
            .item-price {
                align-self: center;
            }
        }

        /* Desktop */
        @media (min-width: 1024px) {
            body {
                padding-top: 200px;
            }
            
            header {
                padding: 1.2rem 0;
            }
            
            .pub-logo {
                height: 150px;
            }
            
            h1 {
                font-size: 3rem;
            }
            
            .subtitle {
                font-size: 1.2rem;
            }
            
            .nav-wrapper {
                top: 180px;
            }
            
            .nav-btn {
                padding: 0.8rem 1.8rem;
                font-size: 0.95rem;
            }
            
            .splash-logo {
                max-width: 400px;
            }
            
            .splash-title {
                font-size: 3rem;
            }
            
            .art-container {
                flex-direction: row;
                justify-content: center;
                gap: 3rem;
            }
            
            .main-art {
                max-width: 400px;
            }
            
            .welcome-art {
                max-width: 320px;
            }
            
            .welcome-text {
                max-width: 450px;
                padding: 2rem;
            }
            
            .items-grid {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .item-content {
                flex-direction: row;
                align-items: center;
                gap: 1.5rem;
            }
            
            .item-price {
                align-self: center;
                min-width: 120px;
            }
            
            .combo-items {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .footer-logos {
                gap: 3rem;
            }
            
            .footer-logo {
                height: 100px;
            }
            
            .pixel-frame-logo {
                height: 90px;
            }
        }

        /* Melhorias de toque para mobile */
        .nav-btn,
        .item-card,
        .scroll-top {
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }
    </style>
</head>
<body>
    <!-- Tela de abertura -->
    <div id="splash-screen" class="splash-screen">
        <img src="https://i.ibb.co/Xxvgw29w/image-removebg-preview-1.png" 
             alt="Madame X" 
             class="splash-logo">
        <h1 class="splash-title">Madame X Pub</h1>
        <p class="splash-subtitle">Cardápio Digital Exclusivo</p>
        <button class="enter-button">ENTRAR</button>
    </div>

    <!-- Header com logo grande -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo-section">
                    <img src="https://i.ibb.co/F4DKVQ0K/492014638-2495221277501933-680649836488517704-n-removebg-preview.png" 
                         alt="Madame X Pub Logo" 
                         class="pub-logo">
                    <div class="header-text">
                        <h1>Madame X Pub</h1>
                        <p class="subtitle">Cardápio Digital Exclusivo</p>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Menu de navegação -->
    <div class="nav-wrapper">
        <div class="nav-container">
            <nav>
                <button class="nav-btn active" data-category="cervejas">
                    🍺 Cervejas
                </button>
                <button class="nav-btn" data-category="drinks">
                    🍸 Drinks
                </button>
                <button class="nav-btn" data-category="caipirinhas">
                    🍋 Caipirinhas
                </button>
                <button class="nav-btn" data-category="doses">
                    🥃 Doses
                </button>
                <button class="nav-btn" data-category="porcoes-frias">
                    🧀 Frias
                </button>
                <button class="nav-btn" data-category="porcoes-quentes">
                    🔥 Quentes
                </button>
                <button class="nav-btn" data-category="comidas">
                    🍽️ Comidas
                </button>
            </nav>
        </div>
    </div>

    <!-- Conteúdo Principal -->
    <main class="container">
        <!-- Arte e boas-vindas ATUALIZADA -->
        <section class="art-section">
            <div class="art-container">
                <img src="https://i.ibb.co/sd3s2Mgh/584053184-1407191308080718-9016196200427794961-n-removebg-preview.png" 
                     alt="Arte Madame X" 
                     class="main-art">
                <img src="https://i.ibb.co/Xxvgw29w/image-removebg-preview-1.png" 
                     alt="Madame X boas-vindas" 
                     class="welcome-art">
                <div class="welcome-text">
                    <h2>Bem-vindos ao Madame X Pub!</h2>
                    <p>Um universo de sabores, drinks especiais e momentos inesquecíveis. Cada item do nosso cardápio foi cuidadosamente selecionado para proporcionar uma experiência única. Explore nossas opções e deixe-se encantar pela magia do Madame X.</p>
                </div>
            </div>
        </section>

        <!-- O restante do conteúdo permanece igual -->
        <!-- Cervejas -->
        <section id="cervejas" class="category active">
            <div class="category-header">
                <div class="category-icon">🍺</div>
                <h2 class="category-title">Cervejas Premium</h2>
            </div>
            
            <div class="subcategory">
                <h3 class="subcategory-title">Garrafas 600ml</h3>
                <div class="items-grid">
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Original 600ml</div>
                                <div class="item-description">Cerveja premium com sabor marcante</div>
                            </div>
                            <div class="item-price">R$ 16,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Amstel 600ml</div>
                                <div class="item-description">Suave e refrescante</div>
                            </div>
                            <div class="item-price">R$ 14,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Heineken 600ml</div>
                                <div class="item-description">Cerveja importada premium</div>
                            </div>
                            <div class="item-price">R$ 18,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Brahma Duplo Malte</div>
                                <div class="item-description">Sabor intenso de malte</div>
                            </div>
                            <div class="item-price">R$ 15,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Império 600ml</div>
                                <div class="item-description">Tradicional e saborosa</div>
                            </div>
                            <div class="item-price">R$ 15,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Fürst 600ml</div>
                                <div class="item-description">Cerveja artesanal alemã</div>
                            </div>
                            <div class="item-price">R$ 28,00</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="subcategory">
                <h3 class="subcategory-title">Long Neck</h3>
                <div class="items-grid">
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Corona Long Neck</div>
                                <div class="item-description">Mexicana premium com limão</div>
                            </div>
                            <div class="item-price">R$ 12,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Império Long Neck</div>
                                <div class="item-description">Garrafa 355ml, tradicional</div>
                            </div>
                            <div class="item-price">R$ 10,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Império Low Carb</div>
                                <div class="item-description">Mesmo sabor, menos carboidratos</div>
                            </div>
                            <div class="item-price">R$ 10,00</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="subcategory">
                <h3 class="subcategory-title">Skol Beats</h3>
                <div class="items-grid">
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Skol Beats Garrafa</div>
                                <div class="item-description">Garrafa 275ml, sabor único</div>
                            </div>
                            <div class="item-price">R$ 12,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Skol Beats Lata G</div>
                                <div class="item-description">Lata 269ml, para quem busca energia</div>
                            </div>
                            <div class="item-price">R$ 12,00</div>
                        </div>
                    </div>
                    <div class="item-card">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Skol Beats Lata P</div>
                                <div class="item-description">Lata compacta, sabor intenso</div>
                            </div>
                            <div class="item-price">R$ 8,00</div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Drinks -->
        <section id="drinks" class="category">
            <div class="category-header">
                <div class="category-icon">🍸</div>
                <h2 class="category-title">Drinks Especiais</h2>
            </div>
            <div class="items-grid">
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Caipicerva</div>
                            <div class="item-description">Cerveja com limão e ingredientes especiais</div>
                        </div>
                        <div class="item-price">R$ 42,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Margarita</div>
                            <div class="item-description">Tequila, triple sec e limão</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Aperol Spritz</div>
                            <div class="item-description">Aperol, espumante e soda</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Gin Tônica Lassaleti</div>
                            <div class="item-description">Gin Lassaleti com especiarias</div>
                        </div>
                            <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Gin Tônica Especial</div>
                            <div class="item-description">Com especiarias e morango fresco</div>
                        </div>
                        <div class="item-price">R$ 32,00</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Caipirinhas -->
        <section id="caipirinhas" class="category">
            <div class="category-header">
                <div class="category-icon">🍋</div>
                <h2 class="category-title">Caipirinhas Orloff</h2>
            </div>
            <div class="items-grid">
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Maracujá com Manga</div>
                            <div class="item-description">Combinação tropical refrescante</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Limão Tradicional</div>
                            <div class="item-description">O clássico brasileiro</div>
                        </div>
                        <div class="item-price">R$ 25,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Morango</div>
                            <div class="item-description">Com morangos frescos</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Yakult</div>
                            <div class="item-description">Cremosa e refrescante</div>
                        </div>
                        <div class="item-price">R$ 26,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Yakult com Morango</div>
                            <div class="item-description">Combinação cremosa com frutas</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Safadinha</div>
                            <div class="item-description">Rúcula, limão e pimenta dedo-de-moça</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Doses -->
        <section id="doses" class="category">
            <div class="category-header">
                <div class="category-icon">🥃</div>
                <h2 class="category-title">Doses Premium</h2>
            </div>
            <div class="items-grid">
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Vodka Smirnoff</div>
                            <div class="item-description">50ml - Tradicional russa</div>
                        </div>
                        <div class="item-price">R$ 18,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Vodka Orloff</div>
                            <div class="item-description">50ml - Nacional premium</div>
                        </div>
                        <div class="item-price">R$ 15,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Whisky Red Label</div>
                            <div class="item-description">50ml - Johnnie Walker</div>
                        </div>
                        <div class="item-price">R$ 22,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Whisky Jack Daniel's</div>
                            <div class="item-description">50ml - Tennessee whiskey</div>
                        </div>
                        <div class="item-price">R$ 25,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Jack Daniel's Honey</div>
                            <div class="item-description">50ml - Com mel</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Jack Daniel's Fire</div>
                            <div class="item-description">50ml - Com canela</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Tequila José Cuervo</div>
                            <div class="item-description">50ml - Tradicional mexicana</div>
                        </div>
                        <div class="item-price">R$ 22,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Campari</div>
                            <div class="item-description">50ml - Amargo italiano</div>
                        </div>
                        <div class="item-price">R$ 18,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Cachaça Premium</div>
                            <div class="item-description">50ml - Nacional selecionada</div>
                        </div>
                        <div class="item-price">R$ 7,00</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Porções Frias -->
        <section id="porcoes-frias" class="category">
            <div class="category-header">
                <div class="category-icon">🧀</div>
                <h2 class="category-title">Porções Frias</h2>
            </div>
            <div class="items-grid">
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Amendoim Japonês</div>
                            <div class="item-description">Porção generosa, crocante</div>
                        </div>
                        <div class="item-price">R$ 7,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Salame Italiano</div>
                            <div class="item-description">Fatiado na hora, qualidade premium</div>
                        </div>
                        <div class="item-price">R$ 25,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Gorgonzola</div>
                            <div class="item-description">Queijo azul italiano, sabor intenso</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Parmesão</div>
                            <div class="item-description">Queijo grana padano, envelhecido</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Provolone</div>
                            <div class="item-description">Queijo defumado, textura única</div>
                        </div>
                        <div class="item-price">R$ 29,00</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Porções Quentes -->
        <section id="porcoes-quentes" class="category">
            <div class="category-header">
                <div class="category-icon">🔥</div>
                <h2 class="category-title">Porções Quentes</h2>
            </div>
            <div class="items-grid">
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Feijão Tropeiro</div>
                            <div class="item-description">Com linguiça, bacon e farofa</div>
                        </div>
                        <div class="item-price">R$ 26,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Quibe Frito</div>
                            <div class="item-description">Crocante por fora, suculento por dentro</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Bolinha de Queijo</div>
                            <div class="item-description">Recheadas com queijo derretido</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Bolinho de Alho Poró</div>
                            <div class="item-description">Com milho e requeijão, sabor diferenciado</div>
                        </div>
                        <div class="item-price">R$ 28,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Caldo de Feijão</div>
                            <div class="item-description">Creme de feijão com torradas</div>
                        </div>
                        <div class="item-price">R$ 26,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Línguiça Recheada</div>
                            <div class="item-description">Com pimenta biquinho, explosão de sabor</div>
                        </div>
                        <div class="item-price">R$ 55,00</div>
                    </div>
                </div>
                <div class="item-card">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Línguiça Especial</div>
                            <div class="item-description">Recheada com rúcula e queijo coalho</div>
                        </div>
                        <div class="item-price">R$ 55,00</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Comidas -->
        <section id="comidas" class="category">
            <div class="category-header">
                <div class="category-icon">🍽️</div>
                <h2 class="category-title">Comidas Especiais</h2>
            </div>
            <div class="items-grid">
                <div class="item-card combo-item">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Tábua de Frios Premium</div>
                            <div class="item-description">Seleção especial para compartilhar</div>
                            <div class="combo-details">
                                <div class="combo-items">
                                    <div class="combo-item-name">Gorgonzola Italiano</div>
                                    <div class="combo-item-name">Parmesão Grana Padano</div>
                                    <div class="combo-item-name">Provolone Defumado</div>
                                    <div class="combo-item-name">Salame Italiano</div>
                                    <div class="combo-item-name">Azeitona Preta</div>
                                    <div class="combo-item-name">Tomatinho Cereja</div>
                                    <div class="combo-item-name">Palmito Pupunha</div>
                                </div>
                            </div>
                        </div>
                        <div class="item-price">R$ 95,00</div>
                    </div>
                </div>
                
                <div class="item-card combo-item">
                    <div class="item-content">
                        <div class="item-info">
                            <div class="item-name">Comida Árabe Completa</div>
                            <div class="item-description">Prato típico da culinária árabe</div>
                            <div class="combo-details">
                                <div class="combo-items">
                                    <div class="combo-item-name">Quibe cru especial</div>
                                    <div class="combo-item-name">Babaganoush (berinjela)</div>
                                    <div class="combo-item-name">Homus Tahine (grão-de-bico)</div>
                                    <div class="combo-item-name">Coalhada seca</div>
                                    <div class="combo-item-name">Pão sírio integral</div>
                                </div>
                            </div>
                        </div>
                        <div class="item-price">R$ 75,00</div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-logos">
                    <img src="https://i.ibb.co/F4DKVQ0K/492014638-2495221277501933-680649836488517704-n-removebg-preview.png" 
                         alt="Madame X Pub Logo" 
                         class="footer-logo">
                    <img src="https://i.ibb.co/Z64Tb7b6/Logo-for-Pixel-Frame-Creative-Agency-removebg-preview.png" 
                         alt="Pixel Frame Creative Agency" 
                         class="footer-logo pixel-frame-logo">
                </div>
                
                <div class="footer-info">
                    <div class="contact-item">
                        <span>📱</span>
                        <span>Pixel Frame Soluções Digitais: (35) 99239-8339</span>
                    </div>
                </div>
                
                <p class="copyright">
                    Cardápio Digital desenvolvido pela Pixel Frame Creative Agency<br>
                    Proibida a venda para menores de 18 anos
                </p>
            </div>
        </div>
    </footer>

    <button class="scroll-top" onclick="scrollToTop()">↑</button>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Tela de abertura
            const splashScreen = document.getElementById('splash-screen');
            const enterButton = document.querySelector('.enter-button');
            
            if (splashScreen) {
                // Esconder a tela de abertura ao clicar no botão
                enterButton.addEventListener('click', function() {
                    splashScreen.classList.add('hidden');
                    // Habilitar scroll após fechar a tela de abertura
                    document.body.style.overflow = 'auto';
                });
                
                // Também permitir fechar tocando em qualquer lugar da tela
                splashScreen.addEventListener('click', function(e) {
                    if (e.target === splashScreen) {
                        splashScreen.classList.add('hidden');
                        document.body.style.overflow = 'auto';
                    }
                });
                
                // Desabilitar scroll enquanto a tela de abertura está visível
                document.body.style.overflow = 'hidden';
            }

            // Navegação por categorias
            const navButtons = document.querySelectorAll('.nav-btn');
            const categories = document.querySelectorAll('.category');
            
            navButtons.forEach(button => {
                button.addEventListener('click', function() {
                    // Remove active de todos
                    navButtons.forEach(btn => btn.classList.remove('active'));
                    
                    // Adiciona active ao clicado
                    this.classList.add('active');
                    
                    // Oculta todas as categorias
                    categories.forEach(category => category.classList.remove('active'));
                    
                    // Mostra categoria correspondente
                    const categoryId = this.getAttribute('data-category');
                    const targetCategory = document.getElementById(categoryId);
                    if (targetCategory) {
                        targetCategory.classList.add('active');
                        
                        // Scroll suave para categoria
                        setTimeout(() => {
                            targetCategory.scrollIntoView({
                                behavior: 'smooth',
                                block: 'start'
                            });
                        }, 100);
                    }
                });
                
                // Feedback tátil para mobile
                button.addEventListener('touchstart', function() {
                    this.style.transform = 'scale(0.95)';
                });
                
                button.addEventListener('touchend', function() {
                    setTimeout(() => {
                        this.style.transform = '';
                    }, 150);
                });
            });

            // Botão scroll to top
            const scrollTopBtn = document.querySelector('.scroll-top');
            
            window.addEventListener('scroll', function() {
                if (window.pageYOffset > 300) {
                    scrollTopBtn.style.display = 'flex';
                } else {
                    scrollTopBtn.style.display = 'none';
                }
            });

            // Melhorias para touch nos cards
            document.querySelectorAll('.item-card').forEach(card => {
                card.addEventListener('touchstart', function() {
                    this.style.opacity = '0.9';
                });
                
                card.addEventListener('touchend', function() {
                    setTimeout(() => {
                        this.style.opacity = '1';
                    }, 150);
                });
            });

            // Otimização para mobile: ajustar scroll da navegação
            const navContainer = document.querySelector('.nav-container');
            if (navContainer) {
                navContainer.addEventListener('touchstart', function(e) {
                    this.style.cursor = 'grabbing';
                });
                
                navContainer.addEventListener('touchend', function(e) {
                    this.style.cursor = 'grab';
                });
            }
        });

        function scrollToTop() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }
    </script>
</body>
</html>
