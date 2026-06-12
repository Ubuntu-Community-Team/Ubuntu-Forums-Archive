---
title: "stop x server"
date: 2007-05-13
forum: General Help
---

### Post by prem1er on 2007-05-13
How do I stop x server so I can install a video driver?

---

### Post by benanzo on 2007-05-13
To stop the X server completely you can simpy do CTRL-ALT-F2.  I would recommend logging out of your current desktop session first so you don't get "Xserver already active on screen 0" errors when you try to restart it.

Just do System > Quit > Log Off
then wait to get to the login screen and hit CTRL-ALT-F2

that will take you to a text console login.  The X server is effectively dead.

To start it again just type startx

---

### Post by prem1er on 2007-05-13
For some reason ctr+alt+f2 is not working.  No terminal opens up, I just lose my cursor until I hit ctr+alt+f9.  Any suggestions?

---

### Post by aysiu on 2007-05-14
Control-Alt-F1 through Control-Alt-F6 do not kill the X server. They just give you a full-screen terminal.

Once you're in that terminal, log in, and type ```
sudo /etc/init.d/gdm stop
``` or, if you're using Kubuntu, type ```
sudo /etc/init.d/kdm stop
``` and that will essentially kill the X server.

---

### Post by strabes on 2007-05-14
You also don't have to kill the X server in order to install video card drivers like you said in your first post.

---

### Post by aysiu on 2007-05-14
> **strabes said:**
> You also don't have to kill the X server in order to install video card drivers like you said in your first post.
Ah, good point.

You will have to temporarily (for a seconds) kill it to reset it and have the changes take effect, though.

---

### Post by benanzo on 2007-05-14
```
sudo /etc/init.d/gdm restart
```
should done after you CTRL-ALT-F2 at the login window (if you followed my bad instructions)

---

