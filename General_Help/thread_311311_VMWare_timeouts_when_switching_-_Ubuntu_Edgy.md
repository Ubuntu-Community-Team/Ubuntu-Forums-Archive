---
title: "VMWare timeouts when switching - Ubuntu Edgy"
date: 2006-12-02
forum: General Help
---

### Post by the_mechanical on 2006-12-02
Hi

Since the installation of Edgy there are timeouts when switching from / to VMWare (Player). These timeouts are about 3-5 seconds.
For example:
switching into Fullscreen -> timeout
switching out -> timeout
and so on (it happens very often).
The problem didn't occur in Dapper.
All other things are running great (except also some timouts in Skype when i get a message/call - but i think this is an other problem).

I hope that someone can help me.
I used the Kernel 2.6.17.10 and now i have tried to compile my own one - same Problem.
It's also no matter of VMWare or VMWare-player.

Ubuntu Edgy (6.10), ATI-Radeon (fglrx, DRI), Athlon64, VMWare-player (1.0.2-2), Kernel 2.6.17.10, Xorg 7.1.1

---

### Post by the_mechanical on 2007-01-15
Ok, no i have the solution: :mrgreen: 

I changed the graphic card from ATI Radeon 9600 to Nvidia 9700 GT. And now - no problem anymore.

So, maybe it was the ati-driver (fglrx) or the configuration :confused:

---

