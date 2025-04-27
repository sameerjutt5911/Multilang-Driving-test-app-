<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ڈرائیونگ ٹیسٹ ایپ</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    select, button { margin-top: 10px; padding: 10px; font-size: 16px; }
    .question { margin-top: 20px; font-size: 20px; }
    .options { margin-top: 10px; }
    .options button { display: block; margin-top: 5px; }
  </style>
</head>
<body>

  <h2>زبان منتخب کریں / Select Language</h2>
  <select id="language" onchange="loadQuestion()">
    <option value="urdu">اردو</option>
    <option value="hindi">हिन्दी</option>
    <option value="english">English</option>
  </select>

  <div class="question" id="questionText"></div>
  <div class="options" id="options"></div>

  <button onclick="nextQuestion()">اگلا سوال / Next Question</button>

  <script>
    const questions = {
      urdu: [
        {
          question: "گاڑی کو پارک کرتے وقت کن باتوں کا خیال رکھنا چاہیے؟",
          options: ["فٹ پاتھ بلاک نہ ہو", "دوسری گاڑی کو نقصان پہنچانا", "سڑک پر کھڑے ہو کر بات کرنا"]
        }
      ],
      hindi: [
        {
          question: "गाड़ी पार्क करते समय किन बातों का ध्यान रखना चाहिए?",
          options: ["फुटपाथ ब्लॉक न हो", "अन्य वाहनों को नुकसान पहुँचाना", "सड़क पर खड़े होकर बातें करना"]
        }
      ],
      english: [
        {
          question: "What should you consider when parking your car?",
          options: ["Do not block the sidewalk", "Damage other vehicles", "Talk while standing on the road"]
        }
      ]
    };

    let currentQuestion = 0;

    function loadQuestion() {
      const lang = document.getElementById('language').value;
      const question = questions[lang][currentQuestion];
      document.getElementById('questionText').innerText = question.question;
      document.getElementById('options').innerHTML = '';
      question.options.forEach(opt => {
        const btn = document.createElement('button');
        btn.innerText = opt;
        document.getElementById('options').appendChild(btn);
      });
    }

    function nextQuestion() {
      // ابھی ایک ہی سوال ہے، بعد میں سوالات بڑھا سکتے ہیں
      alert('مزید سوالات جلد آئیں گے!');
    }

    // پہلی بار لوڈ پر سوال دکھانا
    loadQuestion();
  </script>

</body>
</html>
