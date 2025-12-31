<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mutlu Yıllar Sevgilim!</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: radial-gradient(circle, #1a1a2e, #16213e);
            color: #fff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        /* Kar Tanesi Efekti */
        .snow {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .container {
            z-index: 2;
            background: rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
        }

        h1 {
            font-size: 2.5em;
            margin-bottom: 20px;
            color: #e94560;
        }

        .message {
            display: none;
            font-size: 1.2em;
            line-height: 1.6;
            margin-top: 20px;
            animation: fadeIn 2s ease-in-out;
        }

        button {
            padding: 15px 30px;
            font-size: 1.1em;
            background-color: #e94560;
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.3s, background-color 0.3s;
        }

        button:hover {
            background-color: #ff2e63;
            transform: scale(1.1);
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Kar tanesi animasyonu için JS desteği gerekecek */
    </style>
</head>
<body>

    <canvas class="snow" id="snowCanvas"></canvas>

    <div class="container">
        <h1 id="title">🎄 2026'ya Hazır Mısın?</h1>
        <p id="sub-title">Senin için küçük bir sürprizim var...</p>
        <button onclick="revealMessage()">Hediyeni Aç 🎁</button>
        
        <div id="secretMessage" class="message">
            <p>Canım Sevgilim,</p>
            <p>Bu yıl benim için en güzel hediye senin varlığındı. <br> 
            Yeni yılda da el ele, bol kahkahalı ve aşk dolu günlerimiz olsun. <br>
            Seni çok seviyorum! ❤️</p>
            <p><strong>Mutlu Yıllar! 🥂</strong></p>
        </div>
    </div>

    <script>
        // Kar Yağdırma Efekti
        const canvas = document.getElementById('snowCanvas');
        const ctx = canvas.getContext('2d');
        let width, height, particles;

        function init() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
            particles = [];
            for (let i = 0; i < 200; i++) {
                particles.push({
                    x: Math.random() * width,
                    y: Math.random() * height,
                    vx: Math.random() * 2 - 1,
                    vy: Math.random() * 2 + 1,
                    size: Math.random() * 3 + 1
                });
            }
        }

        function draw() {
            ctx.clearRect(0, 0, width, height);
            ctx.fillStyle = 'rgba(255, 255, 255, 0.😎';
            ctx.beginPath();
            particles.forEach(p => {
                ctx.moveTo(p.x, p.y);
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
            });
            ctx.fill();
            update();
            requestAnimationFrame(draw);
        }

        function update() {
            particles.forEach(p => {
                p.x += p.vx;
                p.y += p.vy;
                if (p.y > height) p.y = -10;
                if (p.x > width) p.x = 0;
                if (p.x < 0) p.x = width;
            });
        }

        window.addEventListener('resize', init);
        init();
        draw();

        // Mesajı Gösterme Fonksiyonu
        function revealMessage() {
            document.getElementById('secretMessage').style.display = 'block';
            document.querySelector('button').style.display = 'none';
            document.getElementById('title').innerText = '❤️ Mutlu Yıllar Birtanem! ❤️';
            document.getElementById('sub-title').style.display = 'none';
        }
    </script>
</body>
</html>
