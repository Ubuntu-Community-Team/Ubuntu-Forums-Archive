---
title: "firestarter gui won't launch"
date: 2006-11-08
forum: General Help
---

### Post by geokok1981 on 2006-11-08
Firestarter worked perfectly until today.
I installed the new nvidia drivers+beryl and since then firestarter gui 
will no launch from the menu.
If I try the terminal I get this error:
"gksudo firestarter
 Xlib: connection to ":0.0" refused by server
 Xlib: No protocol specified


 (firestarter:5000): Gtk-WARNING **: cannot open display:"

The problem occurs in beryl as well as in metacity.
I have an nvidia 5200 and only one monitor connected to it.
 Any clue how to solve this?

****SOLVED****
It turns out that the problem was edititng the sudoers file to make firestarter launch without a password.
I should give usr/bin/firestarter in the path instead of sbin.

---

