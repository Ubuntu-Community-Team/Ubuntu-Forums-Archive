---
title: "terminal wont open after updateing to 15.04"
date: 2015-07-11
forum: General Help
---

### Post by andreadixon825 on 2015-07-11
Hi, I just install Ubuntu 15.04 and my terminal worked grate but then I restarted and now it wont open, how can I get it back. When I click on terminal nothing happens, please help :)

---

### Post by dino99 on 2015-07-11
try ctrl+t or ctrl+alt+t

---

### Post by andreadixon825 on 2015-07-11
Hi, I just tried toughs keys and it still wont open. I don&#8217;t know why this happened.

---

### Post by CitadelUniversal on 2015-07-11
Can you enter the main console mode via ctrl+alt+F1 and then type your username and password and try and reinstall the terminal via sudo apt-get install gnome-terminal or the equivalent to gnome-terminal.... After that do sudo reboot it will then go back to graphical mode.

---

### Post by andreadixon825 on 2015-07-11
Hi, I can get to the console though ctrl+alt+F1 and I uninstalled it and installed it again and I'm still having the problem of it not opening and none of these commands work aether ctrl+t or ctrl+alt+t 				.

---

### Post by tyler.maxwell on 2015-07-12
Two things you might want to try:
1) in virtual console (Ctrl-Alt-F1) ```
which gnome-terminal
``` this should tell you the path to the executable
2) in X try Alt-F2 and if works, type gnome-terminal .

---

### Post by collisionystm on 2015-07-12
open Xterm and type gnome-terminal. Hit enter. Is there an error? I had this happen in Arch once and it was because I forgot to set my Locale. Might be a similar issue?

---

