---
title: "Issue with Path in zsh"
date: 2016-02-19
forum: General Help
---

### Post by JJuel on 2016-02-19
I have recently installed Ubuntu. I have also replaced bash with zsh for my shell. However, I am having an issue adding something to the environment path. I have installed Go, and am looking to add that to my path. So I *export PATH=$PATH:/usr/local/go/* which is where it is installed to. That will work just fine. However, when I try to add that line to my /etc/zsh/zshenv file it does not recognize the go command. How do get this to permanently stay in my zsh?

Thank you!

---

### Post by spjackson on 2016-02-20
What you have described should work, unless you are rewriting PATH in one of your $HOME/.zsh* files.

---

