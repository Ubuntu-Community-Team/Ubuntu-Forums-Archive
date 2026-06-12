---
title: "Xorg doesn't start"
date: 2007-03-02
forum: General Help
---

### Post by pietrob71 on 2007-03-02
Yestarday night I've turn off my pc with Edgy; today when the system show the login window, I insert my login and password and the system seems to start but shows another time the login window. If I go in text mode with CRTL-ALT-F1 login and password are accepted; if I launch Xorg with STARTX, this is the output:

Fatal server error:
Server is already active for display 0.....................
........
......

If I remove /tmp/.X0-lock with rm /tmp/.X0-lock and than STARTX I receive:

Fatal server error:
Caught signal 11. Server aborting

xinit: connection to X server lost
xauth: error in locking authority file /home/pi/.Xauthority

Anyone can help me!?

Thanks in advance

Pietro

---

### Post by tsanoff on 2007-03-02
have you recently changed either the xorg.conf or the gdm files?

---

