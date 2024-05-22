<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Šimone, je ti lépe?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            overflow: hidden;
        }
        .title {
            font-size: 3em;
            color: #333;
            margin-bottom: 20px;
            display: inline-block;
            white-space: nowrap;
        }
        .ascii-art {
            position: relative;
            font-family: 'Courier New', Courier, monospace;
            white-space: pre;
            color: #333;
            margin-bottom: 20px;
            animation: explode-reassemble 5s infinite;
        }
        .ascii-art::before, .ascii-art::after {
            content: attr(data-text);
            position: absolute;
            left: 0;
            top: 0;
            animation: pixelFall 3s infinite;
            color: rgba(51, 51, 51, 0.5);
        }
        .ascii-art::after {
            animation-delay: 1.5s;
        }
        @keyframes shake {
            0%, 100% { transform: translate(0, 0); }
            25% { transform: translate(5px, -5px); }
            50% { transform: translate(-5px, 5px); }
            75% { transform: translate(5px, 5px); }
        }
        @keyframes pixelFall {
            0% { opacity: 1; transform: translateY(0); }
            100% { opacity: 0; transform: translateY(100px); }
        }
        @keyframes explode-reassemble {
            0%, 100% { transform: translate(0, 0); opacity: 1; }
            25% { transform: translate(5px, -5px) scale(0); opacity: 0; }
            50% { transform: translate(-5px, 5px) scale(0); opacity: 0; }
            75% { transform: translate(5px, 5px) scale(0); opacity: 0; }
            100% { transform: translate(0, 0); opacity: 1; }
        }
        .animated {
            animation: multiply 5s infinite;
        }
        @keyframes multiply {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(10); }
        }
        @keyframes bounce {
            0% { transform: translateY(0) rotate(0); }
            50% { transform: translateY(-100px) rotate(360deg); }
            100% { transform: translateY(0) rotate(720deg); }
        }
        .bouncing-image {
            animation: bounce 2s infinite;
        }
        audio {
            display: none;
        }
    </style>
</head>
<body>
    <div class="title">Šimone, je ti lépe?</div>
    <img src="https://media.licdn.com/dms/image/C4D03AQFjYythvqmIPA/profile-displayphoto-shrink_200_200/0/1549064665031?e=1721865600&v=beta&t=hCZb3JhJoXzUTwIRNZpQ_TB06zik39HnXpc0kDfX6kE" alt="Fotografie kolegy" class="bouncing-image" style="width: 200px; border-radius: 50%; margin-bottom: 20px;">
    <div class="ascii-art" data-text="
          _____
         /     \
        |  o o  |
        |  \_/  |
         \_____/
        /|||||||\
       / | | | | \
      /  | | | |  \
         (     )
          | | |
          | | |">
        <pre>
          _____
         /     \
        |  o o  |
        |  \_/  |
         \_____/
        /|||||||\
       / | | | | \
      /  | | | |  \
         (     )
          | | |
          | | |
        </pre>
    </div>
    <audio controls autoplay loop>
        <source src="hudba.mp3" type="audio/mpeg">
        Váš prohlížeč nepodporuje přehrávání audio souborů.
    </audio>
    <script>
        // Funkce pro zpoždění animace spojování textu
        function delayAnimation() {
            const asciiArt = document.querySelector('.ascii-art');
            const text = asciiArt.dataset.text;
            asciiArt.innerHTML = '';
            text.split('').forEach(char => {
                const span = document.createElement('span');
                span.textContent = char;
                asciiArt.appendChild(span);
                setTimeout(() => {
                    span.style.opacity = 1;
                }, Math.random() * 2000);
            });
        }
        // Spustí animaci spojování textu po 2 sekundách
        setTimeout(delayAnimation, 2000);

        // Zpoždění animace množení postavy
        setTimeout(() => {
            const asciiArt = document.querySelector('.ascii-art');
            asciiArt.classList.add('animated');
        }, 5000);
    </script>
</body>
</html>
