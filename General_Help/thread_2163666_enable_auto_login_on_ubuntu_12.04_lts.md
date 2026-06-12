---
title: "enable auto login on ubuntu 12.04 lts"
date: 2013-07-19
forum: General Help
---

### Post by pegi on 2013-07-19
[COLOR=#000000][FONT=times new roman]Dear friends
[/FONT][/COLOR]
I need to enable auto login on LXC(Ubuntu 12.04 lts) 
i have  tested the some commands for 12.04 but i do not know why it does not working...

thank you so much for your attention and cooperation in advance

---

### Post by dino99 on 2013-07-19
oops

---

### Post by dino99 on 2013-07-19
open a terminal to set your settings:

> sudo gedit /etc/lightdm/lightdm.conf
add the content below:

autologin-user=yourusername
autologin-user-timeout=0

---

### Post by dino99 on 2013-07-19
open a terminal to set your settings:

> sudo gedit /etc/lightdm/lightdm.conf
add the content below:

autologin-user=username
autologin-user-timeout=0

---

