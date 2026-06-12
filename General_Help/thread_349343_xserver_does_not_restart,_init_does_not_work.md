---
title: "xserver does not restart, init does not work"
date: 2007-01-30
forum: General Help
---

### Post by DaOane on 2007-01-30
Ubuntu 6.10, 2.6.17-10-386, Radeon 9200 Mobility, fglrx drivers

Hello!

I can't restart the x-server, the screen gets black but X does not start up again. When I log out gnome shuts down until the background image is left and the computer hangs up - I can't even kill the x-server. Shutdown works fine. I tried to manually go down to runlevel 3, but the command sudo init 3 is just ignored - nothing happens.
Any help is appreciated! Thank you!

Henning

---

### Post by mizar001 on 2007-01-30
To kill the xserver process you must have access to another tty (CTRL-ALT-F1) and kill from terminal, and return to your default tty (F7).

I recommend you to re-configure the xserver and see if, without radeon drivers, the problem happens.

---

