---
title: "ATI Driver - Disabling Composite Causes Crash"
date: 2006-12-11
forum: General Help
---

### Post by joey7855 on 2006-12-11
Hello! I'm having a little problem with my ATI (fglrx) drivers. Using the ones off the repositories (8.28.8) I have been able to use XGL, Beryl and everything on my ATI Xpress 200m. However, I woke up this morning and now when I boot up my computer I get nothing but a black screen (backlight still on) and am not able to Ctrl+Alt+F1 in to a terminal.

After banging my head a few times trying to figure it out I did a complete reinstallation of Edgy to find the same problem after installing the fglrx drivers and changing the Xorg configuration file.

I've pinpointed the problem to the Extensions section. If I disable the Composite extension, the crash happens. However, if I comment or remove that line, X and Gnome start up fine, but I don't have DRI. Any help would be greatly appreciated!

HP Pavilion zv6000 Laptop
AMD Athlon 64 3200+
1GB RAM
ATI Xpress 200m (128mb Dedicated VRAM, 128mb Shared)

---

### Post by peppy.ch on 2006-12-11
Hello, 
I had the same problem with my ATI mobility radeon 9000. In order to fix it I had to remove the fglrx driver and install the windows driver with ndiswrapper.
Before that you do this try to look on the ATI home page they published sum linux driver. If not I think you will have to use ndiswrapper, this is not ideal but it works ;)
I hope this will help you

---

### Post by joey7855 on 2006-12-11
It was my impression that ndiswrapper was for network interfaces. My problem deals with the graphics card. Now I'm really confused! :-|

---

### Post by peppy.ch on 2006-12-11
mmmmmmmmm I used sow many tools to fix my problems sorry for that you want install your graphic with ndis ](*,)
let me look wich tool I used and I mail back sorry

---

### Post by Hygelac on 2006-12-11
I have the same computer.  You might 'want' to enter the BIOS and tell it to use only shared memory (UMA ONLY).  I have to do that to get it to work with DRI (and to avoid that blank screen you mentioned).

---

### Post by Dragonstar on 2007-01-11
I just came back from 3 week visit to my parents and found out that now I have this exact same problem.  Any ideas what causes it?

AMD Athlon 64 3200+
1GB RAM
ATI Radeon 9800 Pro 128mb

---

