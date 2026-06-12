---
title: "Notification box theme broken"
date: 2016-12-20
forum: General Help
---

### Post by atomic44 on 2016-12-20
After installing nvidia drivers on my Ubuntu 16.04.1 (using additional drivers from Ubuntu menus), my notification box is broken. Does anybody know what could possibly go wrong? 
I can't now see notification box when changing volume. Other notifications looks like this one below.

[ATTACH=CONFIG]272774[/ATTACH]

Thank you in advance.

---

### Post by atomic44 on 2016-12-20
Ok, finally solved the problem. If anyone will be facing same problem, it's because if you install also i3 wm (which i use for dev work), it installs dunst. apt remove dunst and killall dunst solves the problem.

---

### Post by ajgreeny on 2016-12-20
Well done! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

