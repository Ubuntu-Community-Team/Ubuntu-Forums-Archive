---
title: "GeForce 6600GT + nVidia Driver = Black Screen"
date: 2007-07-02
forum: General Help
---

### Post by andrejkw on 2007-07-02
Hello,

I installed Fiesty couple hours ago, however I am having a really serious problem with my nVidia graphics card. Whenever I install the nVidia driver (nvidia-glx, nvidia-glx-new, or the latest nvidia.com driver), Ubuntu freezes when xorg loads up. I only get a black screen and nothing else, Ctrl+Alt+Backspace and Ctrl+Alt+F2 don't do anything. Even the HDD led isn't indicating any activity. Things work fine with the nv driver though, however I get no acceleration. The Xorg.0.log doesn't get updated either when used with any driver other than nv.

My hardware:
Intel Pentium 4 (Prescott) 3.2GHz with HT
ECS 915G-A (V1.2A)
GeForce 6600GT 256MB (on AGP-Express)

Everything fine on Windows with the nVidia drivers.
Thanks!, hopefully someone will solve my problem.

Ondrej,

---

### Post by hardyn on 2007-07-02
publish your xorg.conf file please

---

### Post by andrejkw on 2007-07-02
Never mind :) I got it fixed. Since the "AGP Express" port isn't really an AGP port, it's really a PCI port which acts like an AGP port, which confused the default AGPGart driver. So, adding **Option "NvAGP" "1"** to xorg.conf, as suggested by my friend worked! :)

---

