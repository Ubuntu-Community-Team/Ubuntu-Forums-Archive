---
title: "Xubuntu Screen Resolution"
date: 2013-09-06
forum: General Help
---

### Post by cuoops on 2013-09-06
Xfce Xubuntu Ubuntu 12.04.3 
I can't get my screen resolution back to how it was before I unplugged my 20 inch HP widescreen monitor and changed my laptop resolution. How do I delete the external monitor profile and start over? It works perfect in the guest account. I went into the settings manager and set everything the same (as in the guest account) in "appearance", "desktop", and "display". It works ok (squishy looking though) in 16 x 1900 but i want 1024 x 768 like it it in the guest account. Everything is off the right and bottom of the screen. I tried     sudo rm /etc/X11/xorg.conf    in terminal emulator and no such file exists. Same thing with     ~/.config/monitors.xml    . I also went into settings editor and "reset property" for the external monitor. Oh yeah, I did a command to see my drivers and it's all correct for my Intel video. I'm pretty new to ubuntu/linux..thanks.

---

### Post by cuoops on 2013-09-06
I got it. I changed my laptop screen to a lower resolution and my external is back to normal.

---

