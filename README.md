# chatting-web-app-
using web technology HTML,CSS,JS code
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Web Chat App</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body {
    height: 100vh;
    background: linear-gradient(135deg, #667eea, #764ba2);
    display: flex;
    justify-content: center;
    align-items: center;
}

/* Chat Container */
.chat-container {
    width: 360px;
    height: 520px;
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(15px);
    border-radius: 20px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.3);
    display: flex;
    flex-direction: column;
    overflow: hidden;
}

/* Header */
.chat-header {
    padding: 15px;
    text-align: center;
    background: rgba(255,255,255,0.2);
    color: #fff;
    font-weight: 600;
    font-size: 18px;
}

/* Chat Area */
.chat-box {
    flex: 1;
    padding: 15px;
    overflow-y: auto;
}

/* Messages */
.message {
    max-width: 75%;
    padding: 10px 14px;
    margin: 8px 0;
    border-radius: 15px;
    font-size: 14px;
    animation: fadeIn 0.3s ease;
}

.sent {
    background: linear-gradient(135deg, #ff512f, #dd2476);
    color: white;
    margin-left: auto;
    border-bottom-right-radius: 5px;
}

.received {
    background: white;
    color: #333;
    margin-right: auto;
    border-bottom-left-radius: 5px;
}

.time {
    font-size: 10px;
    opacity: 0.7;
    margin-top: 3px;
    text-align: right;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}

/* Input Area */
.chat-input {
    display: flex;
    padding: 10px;
    background: rgba(255,255,255,0.2);
}

.chat-input input {
    flex: 1;
    padding: 10px 12px;
    border-radius: 12px;
    border: none;
    outline: none;
    font-size: 14px;
}

.chat-input button {
    margin-left: 8px;
    border: none;
    width: 45px;
    border-radius: 50%;
    background: linear-gradient(135deg, #43cea2, #185a9d);
    color: white;
    font-size: 18px;
    cursor: pointer;
    transition: 0.3s;
}

.chat-input button:hover {
    transform: scale(1.1);
}
</style>
</head>

<body>

<div class="chat-container">
    <div class="chat-header">💬 Web Chat</div>

    <div class="chat-box" id="chatBox">
        <div class="message received">
            Hello! 👋
            <div class="time">10:00 AM</div>
        </div>
    </div>

    <div class="chat-input">
        <input type="text" id="messageInput" placeholder="Type a message...">
        <button onclick="sendMessage()">➤</button>
    </div>
</div>

<script>
function sendMessage() {
    const input = document.getElementById("messageInput");
    const chatBox = document.getElementById("chatBox");

    if (input.value.trim() === "") return;

    const messageDiv = document.createElement("div");
    messageDiv.classList.add("message", "sent");
    messageDiv.innerHTML = `
        ${input.value}
        <div class="time">${new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</div>
    `;

    chatBox.appendChild(messageDiv);
    input.value = "";
    chatBox.scrollTop = chatBox.scrollHeight;

    // Auto reply demo
    setTimeout(() => {
        const reply = document.createElement("div");
        reply.classList.add("message", "received");
        reply.innerHTML = `
            Nice message 😊
            <div class="time">${new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</div>
        `;
        chatBox.appendChild(reply);
        chatBox.scrollTop = chatBox.scrollHeight;
    }, 800);
}
</script>

</body>
</html>

