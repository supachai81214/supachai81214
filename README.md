- 👋 Hi, I’m @supachai81214
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
supachai81214/supachai81214 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
// Say command: read text aloud
function say(text) {
  speechSynthesis.speak(new SpeechSynthesisUtterance(text))
}

// Find the most recent reply
function lastReply() {
  const replies = document.getElementsByClassName('prose')
  const last = replies[replies.length - 1]
  return last.textContent
}

// Register a sayLast function to the global window so we can call it later.
window.sayLast = () => say(lastReply())

// Register hotkey Cmd+S (Ctrl+S on Windows) to start/stop
document.addEventListener('keydown', function (event) {
  // Ctrl + S or Cmd + S hotkey
  if ((event.ctrlKey || event.metaKey) && event.key === 's') {
    if (speechSynthesis.speaking) {
      speechSynthesis.cancel()
    } else {
      sayLast()
    }

    event.preventDefault() // Prevent the default action of saving the page
  }
})
console.log('sayLast() 🔈 function installed, Cmd + S hotkey to activate')
