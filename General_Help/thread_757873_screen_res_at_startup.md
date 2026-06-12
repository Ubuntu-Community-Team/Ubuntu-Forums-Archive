---
title: "screen res at startup"
date: 2008-04-17
forum: General Help
---

### Post by Kalidor on 2008-04-17
Kubuntu 7.10 64 bit. Samsung 2232bw recently purchased (had another screen before. Although I manually change the resolution after every boot to 1680x1050 through nvidia xserver settings and it works, I can't seem to make the system boot with this resolution. It boots at 1280x1024 like which is the resolution i used with the previous screen.
What can i do?

---

### Post by wolfen69 on 2008-04-17
try in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then ctrl-alt-backspace to reset x.

---

### Post by Kalidor on 2008-04-17
yes. But this leads to black screen (no signal) right after reboot.

---

### Post by Kalidor on 2008-04-17
any idea?

---

