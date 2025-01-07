  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 600px;
            margin: 50px auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #333;
        }
        form {
            text-align: center;
        }
        label {
            display: block;
            margin-bottom: 10px;
            color: #666;
        }
        input[type="number"],
        input[type="text"],
        button {
            padding: 10px;
            width: 100%;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            background-color: #4caf50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            background-color: #f9f9f9;
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
        }
        .result p {
            margin: 10px 0;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Temperature Converter</h1>
        <form id="converter-form">
            <label for="temperature">Enter temperature:</label>
            <input type="number" id="temperature" required>
            <label for="unit">Enter unit (C/F/K):</label>
            <input type="text" id="unit" maxlength="1" required>
            <button type="button" onclick="convertTemperature()">Convert</button>
        </form>
        <div class="result" id="result" style="display: none;">
            <h2>Conversion Result</h2>
            <p id="celsius">Temperature in Celsius: <span></span></p>
            <p id="fahrenheit">Temperature in Fahrenheit: <span></span></p>
            <p id="kelvin">Temperature in Kelvin: <span></span></p>
            <button onclick="resetForm()">Reset</button>
        </div>
    </div>

    <script>
        function convertTemperature() {
            var temperature = parseFloat(document.getElementById("temperature").value);
            var unit = document.getElementById("unit").value.toUpperCase();
            var celsius, fahrenheit, kelvin;

            if (unit === "C") {
                celsius = temperature;
                fahrenheit = (temperature * 9/5) + 32;
                kelvin = temperature + 273.15;
            } else if (unit === "F") {
                celsius = (temperature - 32) * 5/9;
                fahrenheit = temperature;
                kelvin = (temperature - 32) * 5/9 + 273.15;
            } else if (unit === "K") {
                celsius = temperature - 273.15;
                fahrenheit = (temperature - 273.15) * 9/5 + 32;
                kelvin = temperature;
            } else {
                alert("Invalid unit. Please enter C, F, or K.");
                return;
            }

            document.getElementById("celsius").querySelector("span").textContent = "Temperature in Celsius: " + celsius.toFixed(2);
            document.getElementById("fahrenheit").querySelector("span").textContent = "Temperature in Fahrenheit: " + fahrenheit.toFixed(2);
            document.getElementById("kelvin").querySelector("span").textContent = "Temperature in Kelvin: " + kelvin.toFixed(2);
            document.getElementById("result").style.display = "block";
        }

        function resetForm() {
            document.getElementById("converter-form").reset();
            document.getElementById("result").style.display = "none";
        }
    </script>
</body>
</html>
