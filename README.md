<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Simple Interest & Amount Calculator</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px;
      background: #f4f4f4;
    }

    .calculator {
      background: white;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
      max-width: 480px;
      width: 100%;
    }

    h2 {
      margin-top: 0;
      color: #333;
      text-align: center;
    }

    label {
      display: block;
      margin-top: 12px;
      font-weight: bold;
    }

    input, select, button {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border-radius: 8px;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }

    select {
      background-color: #eee;
    }

    button {
      margin-top: 15px;
      background-color: #0077cc;
      color: white;
      font-weight: bold;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #005fa3;
    }

    #result {
      margin-top: 15px;
      font-size: 1.1em;
      text-align: center;
      color: #007700;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <h2>Simple Interest & Amount Calculator</h2>

    <label for="unknown">I want to solve for:</label>
    <select id="unknown">
      <option value="interest">Interest (I)</option>
      <option value="principal">Principal (P)</option>
      <option value="rate">Rate (R)</option>
      <option value="time">Time (T)</option>
      <option value="amount">Amount (S)</option>
    </select>

    <label for="principal">Principal (P):</label>
    <input type="number" id="principal" placeholder="e.g. 1000" />

    <label for="rate">Rate (% per year):</label>
    <input type="number" id="rate" placeholder="e.g. 5" />

    <label for="time">Time (years):</label>
    <input type="number" id="time" placeholder="e.g. 2" />

    <label for="interest">Interest (I):</label>
    <input type="number" id="interest" placeholder="e.g. 100" />

    <label for="amount">Amount (S):</label>
    <input type="number" id="amount" placeholder="e.g. 1100" />

    <button onclick="solveSI()">Solve</button>
    <p id="result"></p>
  </div>

  <script>
    function solveSI() {
      const unknown = document.getElementById("unknown").value;
      const P = parseFloat(document.getElementById("principal").value);
      const R = parseFloat(document.getElementById("rate").value);
      const T = parseFloat(document.getElementById("time").value);
      const I = parseFloat(document.getElementById("interest").value);
      const S = parseFloat(document.getElementById("amount").value);
      let result = "";

      switch (unknown) {
        case "interest":
          if (isNaN(P) || isNaN(R) || isNaN(T)) {
            result = "Please provide P, R, and T.";
          } else {
            const interest = (P * R * T) / 100;
            result = `Interest (I) = RM ${interest.toFixed(2)}`;
          }
          break;

        case "principal":
          if (isNaN(I) || isNaN(R) || isNaN(T)) {
            result = "Please provide I, R, and T.";
          } else {
            const principal = (I * 100) / (R * T);
            result = `Principal (P) = RM ${principal.toFixed(2)}`;
          }
          break;

        case "rate":
          if (isNaN(I) || isNaN(P) || isNaN(T)) {
            result = "Please provide I, P, and T.";
          } else {
            const rate = (I * 100) / (P * T);
            result = `Rate (R) = ${rate.toFixed(2)}%`;
          }
          break;

        case "time":
          if (isNaN(I) || isNaN(P) || isNaN(R)) {
            result = "Please provide I, P, and R.";
          } else {
            const time = (I * 100) / (P * R);
            result = `Time (T) = ${time.toFixed(2)} years`;
          }
          break;

        case "amount":
          if (isNaN(P) || isNaN(R) || isNaN(T)) {
            result = "Please provide P, R, and T.";
          } else {
            const amount = P * (1 + (R * T) / 100);
            result = `Amount (S) = RM ${amount.toFixed(2)}`;
          }
          break;

        default:
          result = "Something went wrong.";
      }

      document.getElementById("result").innerText = result;
    }
  </script>
</body>
</html>
