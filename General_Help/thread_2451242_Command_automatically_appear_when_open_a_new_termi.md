---
title: "Command automatically appear when open a new terminal"
date: 2020-09-29
forum: General Help
---

### Post by edwin4project on 2020-09-29
Hi how can I stop these commands from appearing everytime I open a new terminal? I tried doing $ sudo nano /etc/bash.bashrc however I can't seem to find the listed command there as well. It would be great if anyone can advice me on how to remove this please!

 [ATTACH=CONFIG]287055[/ATTACH]

---

### Post by Impavidus on 2020-09-30
You can simply copy the text from the terminal and paste it in your post. Much easier to do and to read than taking a picture of your screen.

ubuntu is the username you get in a live session. Have you installed with that username or is this a live session?

LD_LIBRARY_PATH looks like a variable, not like a command. Most likely there are some syntax errors (like missing $ signs) in some file loaded by bash during initialisation. Have you checked ~/.bashrc and ~/.profile?

---

### Post by CelticWarrior on 2020-09-30
And is this RPi running Ubuntu-Mate?

---

