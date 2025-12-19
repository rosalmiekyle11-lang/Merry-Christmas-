# Merry-Christmas-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Merry Christmas</title>
  <style>
    body {
      margin: 0;
      min-height: 100vh;
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      font-family: 'Georgia', serif;
      color: #fff;
      padding: 20px;
    }

    .countdown {
      font-size: 1.2rem;
      font-weight: bold;
      margin-bottom: 20px;
      background: rgba(255,255,255,0.15);
      padding: 10px 20px;
      border-radius: 10px;
    }

    .container {
      text-align: center;
    }

    .envelope {
      width: 200px;
      height: 150px;
      background: #fff;
      margin: auto;
      border-radius: 8px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
      position: relative;
      cursor: pointer;
      transition: transform 0.3s;
    }

    .envelope:hover {
      transform: scale(1.05);
    }

    .flap {
      position: absolute;
      top: 0;
      left: 0;
      width: 0;
      height: 0;
      border-left: 100px solid transparent;
      border-right: 100px solid transparent;
      border-bottom: 60px solid #fff;
      border-radius: 0 0 8px 8px;
    }

    .letter {
      display: none;
      margin-top: 20px;
      width: 300px;
      max-width: 90vw;
      padding: 20px;
      background: #fff;
      border-radius: 8px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
      text-align: left;
      white-space: pre-line;
      color: #333;
    }

    .final {
      display: none;
      margin-top: 20px;
      font-weight: bold;
      color: #7b1e1e;
    }
  </style>
</head>
<body>

  <div class="countdown" id="countdown">0 days, 0 hours, 0 minutes since we met</div>

  <div class="container">
    <div class="envelope" onclick="openEnvelope()">
      <div class="flap"></div>
      <p style="position:absolute; top:60px; width:100%; text-align:center; font-weight:bold; color:#203a43;">📩 Click me</p>
    </div>

    <div class="letter" id="letter"></div>
    <div class="final" id="finalMessage">✨ I’m really glad I met you. ✨</div>
  </div>

  <script>
    // ===== Countdown since you met =====
    const firstMet = new Date("2025-11-22T12:00:00"); // change to the exact date/time you met

    function updateCountdown() {
      const now = new Date();
      let diff = now - firstMet;

      const days = Math.floor(diff / (1000*60*60*24));
      diff -= days * (1000*60*60*24);

      const hours = Math.floor(diff / (1000*60*60));
      diff -= hours * (1000*60*60);

      const minutes = Math.floor(diff / (1000*60));

      document.getElementById("countdown").textContent =
        `${days} days, ${hours} hours, ${minutes} minutes since we met`;
    }

    updateCountdown();
    setInterval(updateCountdown, 60000); // updates every minute

    // ===== Letter typing =====
    const text = `Haiii, Merry Christmas 🎄

I know we’ve only known each other for a short time, but I’m really glad I met you. Somehow, you made my days feel more interesting and lighter—parang ang hirap i-explain, pero may something. I find you genuinely interesting, and I’m honestly willing to get to know you more, little by little.

Hindi pa New Year pero isasama ko na ’to kasi… katamad gumawa ng panibago 😭 HAHAHA. But seriously, I hope the world treats you gently. Sana mas maging kind ang mga susunod na araw sa’yo, and that next year brings you more happiness, peace, and moments that make you feel safe and appreciated.

Take care always. I’m really glad you exist.`;

    let index = 0;

    function openEnvelope() {
      document.querySelector('.envelope').style.display = 'none';
      const letterDiv = document.getElementById('letter');
      letterDiv.style.display = 'block';

      const finalMessage = document.getElementById('finalMessage');

      const interval = setInterval(() => {
        letterDiv.textContent += text[index];
        index++;
        if (index >= text.length) {
          clearInterval(interval);
          finalMessage.style.display = 'block';
        }
      }, 30);
    }
  </script>

</body>
</html>
