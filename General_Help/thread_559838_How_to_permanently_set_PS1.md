---
title: "How to permanently set PS1?"
date: 2007-09-25
forum: General Help
---

### Post by demagogue on 2007-09-25
I'm trying to permanently change the command prompt in gnome-terminal. Simply typing 'PS1="insert prompt here"' doesn't work. It'll change the prompt, but only until I exit the terminal. Then when I start up another terminal, it goes back to the standard "user@home" prompt. I've tried monkeying around with .bashrc, but can't get it to display plain text. It always displays either "echo "prompt" " or "prompt", and I want it to just print the text without quotes. What do I need to change?

---

### Post by ddrichardson on 2007-09-25
You need to edit to .bashrc:```
export $PS1='insert prompt here'
```There's examples in man bash, search for PS1

---

### Post by demagogue on 2007-09-27
Thanks. I fixed it. Turned out to be a simple quotation error. I'm new to Ubuntu.

---

