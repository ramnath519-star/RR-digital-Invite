<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Rishitha ❤️</title>
    <style>
        body {
            background-color: #ffe4e1;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Segoe UI', Tahoma, sans-serif;
            overflow: hidden; 
        }

        /* Falling Hearts Animation */
        .falling-heart {
            position: fixed;
            top: -10px;
            color: #ff6b81;
            font-size: 20px;
            user-select: none;
            z-index: -1;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to {
                transform: translateY(105vh) rotate(360deg);
            }
        }

        .card {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 3rem;
            border-radius: 25px;
            box-shadow: 0 15px 35px rgba(233, 30, 99, 0.2);
            text-align: center;
            width: 350px;
            backdrop-filter: blur(8px);
            z-index: 10;
            border: 2px solid #fff;
        }

        .heart-main {
            color: #e91e63;
            font-size: 65px;
            animation: beat 0.8s infinite alternate;
            margin-bottom: 15px;
        }

        @keyframes beat {
            from { transform: scale(1); }
            to { transform: scale(1.15); }
        }

        h1 {
            color: #333;
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        .btn-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
            height: 50px; /* Space for the absolute button */
        }

        button {
            padding: 12px 28px;
            border-radius: 50px;
            border: none;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        #yes-btn {
            background-color: #e91e63;
            color: white;
            z-index: 11;
        }

        #no-btn {
            background-color: #ff9a9e;
            color: white;
            position: absolute;
        }

        #hidden-message {
            display: none;
            margin-top: 20px;
            color: #e91e63;
            font-weight: bold;
            font-size: 1.6rem;
            line-height: 1.4;
        }
    </style>
</head>
<body>

    <div class="card">
        <div class="heart-main">❤️</div>
        <h1 id="question">Rishitha, will you be my Valentine?</h1>
        
        <div class="btn-container" id="actions">
            <button id="yes-btn" onclick="sayYes()">Yes!</button>
            <button id="no-btn" onmouseover="moveButton()" onclick="moveButton()">No</button>
        </div>

        <div id="hidden-message">I knew you'd say yes, Rishitha! 🥰🌹<br>Can't wait!</div>
    </div>

    <script>
        // Makes the "No" button jump away
        function moveButton() {
            const btn = document.getElementById('no-btn');
            // Ensure button stays within visible window
            const x = Math.random() * (window.innerWidth - btn.offsetWidth);
            const y = Math.random() * (window.innerHeight - btn.offsetHeight);
            
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
            btn.style.position = 'fixed';
        }

        // Action when she clicks Yes
        function sayYes() {
            document.getElementById('actions').style.display = 'none';
            document.getElementById('question').innerText = "Yay! ❤️";
            document.getElementById('hidden-message').style.display = 'block';
            
            // Celebration: shower of hearts!
            setInterval(createHeart, 100);
        }

        // Falling hearts logic
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('falling-heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.animationDuration = Math.random() * 2 + 3 + "s";
            heart.style.opacity = Math.random();
            heart.style.fontSize = Math.random() * 20 + 10 + "px";
            
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 5000);
        }

        // Subtle background hearts on load
        setInterval(createHeart, 600);
    </script>
</body>
</html>
