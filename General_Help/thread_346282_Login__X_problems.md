---
title: "Login / X problems"
date: 2007-01-25
forum: General Help
---

### Post by gtijon on 2007-01-25
I've managed to install Ubuntu 6.10 with the alternate CD (the live CD gave me the same issue as I'm getting now).

The system boots fine, but when I login, no matter if I choose GNOME, Failsafe GNOME or command prompt, something dies and throws me back to the login screen after a few seconds.

The hardware is as follows:

Asus P2B motherboard,
Pentium III 550
320 megs of RAM of unknown provenance (memtested and came out fine)
Old Maxtor HD
Voodoo 3 2000 (IIRC, definately a V3, not entirely sure of the model, but that only affects the clock speed of it anyway) - This is where I suspect the problems are cropping up as I remember it being a bit difficult back when I used Debian.

Any ideas - I assume this all logs somewhere and there's a way for me to get a command line so I can post some useful info?

---

### Post by gtijon on 2007-01-25
Fixed it with some x-config meddling. dpkg-reconfigure xserver-xorg, selecting vesa rather than Voodoo...

---

