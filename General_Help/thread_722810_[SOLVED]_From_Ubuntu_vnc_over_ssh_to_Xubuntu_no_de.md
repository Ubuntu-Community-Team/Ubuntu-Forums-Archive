---
title: "[SOLVED] From Ubuntu vnc over ssh to Xubuntu: no desktop panels etc."
date: 2008-03-12
forum: General Help
---

### Post by whoop on 2008-03-12
I've been trying to setup a vnc connection through ssh tunneling, from a ubuntu machine to a xubuntu machine. I used this tutorial:
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

So I use vncviewer, ssh and tightvncserver.
I get everything up and running without any noticeable errors. But when I start vncviewer it pops up a screen with just a terminal inside. I can launch applications via the terminal and the all function properly but I get no "real" desktop. Did I mis a step or something.

Please view attached screen shot if my description of the problem is not clear...

---

### Post by whoop on 2008-03-12
Oops very silly of me, I figured it out myself. I did not config ~/.vnc/xstartup yet.
[SOLVED]

---

