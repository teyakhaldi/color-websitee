# color-websitee
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اكتشف لون اسمك!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
            background-color: #f4f4f4;
        }
        input {
            padding: 10px;
            font-size: 18px;
            margin: 10px;
        }
        button {
            padding: 10px;
            font-size: 18px;
            cursor: pointer;
        }
        #colorBox {
            width: 200px;
            height: 200px;
            margin: 20px auto;
            display: none;
            border-radius: 10px;
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
        }
    </style>
</head>
<body>

    <h1>اكتب اسمك واكتشف لونك الخاص!</h1>
    <input type="text" id="nameInput" placeholder="أدخل اسمك هنا">
    <button onclick="generateColor()">اكتشف اللون</button>
    <div id="colorBox"></div>
    <p id="colorCode"></p>

    <script>
        function nameToColor(name) {
            let hash = 0;
            for (let i = 0; i < name.length; i++) {
                hash = name.charCodeAt(i) + ((hash << 5) - hash);
            }
            let color = "#";
            for (let i = 0; i < 3; i++) {
                let value = (hash >> (i * 8)) & 0xFF;
                color += ("00" + value.toString(16)).substr(-2);
            }
            return color;
        }

        function generateColor() {
            let name = document.getElementById("nameInput").value.trim();
            if (name === "") {
                alert("الرجاء إدخال اسم!");
                return;
            }
            let color = nameToColor(name);
            document.getElementById("colorBox").style.backgroundColor = color;
            document.getElementById("colorBox").style.display = "block";
            document.getElementById("colorCode").innerText = لونك: ${color};
        }
    </script>
<div id="colorBox" style="width: 200px; height: 200px; margin: 20px auto; display: none; border-radius: 10px;"></div>
<p id="colorCode"></p>
</body>
</html>
