---
title: "Problem running Xmon"
date: 2008-05-26
forum: General Help
---

### Post by KeithSloan on 2008-05-26
I am having problems running Xmon on Ubuntu 8.04

From one terminal I run
xmonui -display :0 | xmond -server :0 -port 9

On another terminal I run 
xhost +Ubuntu ( Ubuntu is my Hostname )
xclock -display localhost:9

All I get is "Can't open connection to Server (ECONNREFUSED)"

Tried various other combinations of xhost but still get Connection refused.

---

### Post by bryceharrington on 2008-10-09
In /etc/gdm/gdm.conf, allow TCP sessions:

 DisallowTCP=false

Beyond that, here's some more detailed instructions:

 [http://mailman.linuxchix.org/pipermail/techtalk/2004-November/019448.html](http://mailman.linuxchix.org/pipermail/techtalk/2004-November/019448.html)

---

