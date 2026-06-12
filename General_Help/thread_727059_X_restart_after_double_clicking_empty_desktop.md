---
title: "X restart after double clicking empty desktop"
date: 2008-03-17
forum: General Help
---

### Post by ianoshorty on 2008-03-17
Hey all.

Im relatively new to linux though determined in my quest to make it a viable option against windows for me.I have it a bit of a snag however and so here i am asking for some help.

I used [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) to install the latest ati drivers and have managed to get them running, Im using a dual monitor setup (dual head) but after installing the driver i have hit a bit of a snag. The driver works fine and everything works, except if i double click on an empty piece of desktop. For some reason this seems to cause X to restart, and i loose everything and have to login again. I should note it is only X, and not the system that restarts.

Anyone have any ideas how to solve this. Il be happy to provide any system details need.

Also, while im here, i have got dual view to work but at startup the monitors are "the wrong way round" so to speek, and i have to use the  aticonfig --swap-monitor command in terminal to get them the right way round after every boot. Is there any way i can get this to be permanent?

Cheers for the help all, Ian.

---

### Post by ianoshorty on 2008-03-17
Ok i have fixed the desktop orientation problem, now just the X restarts. Anyone got any ideas for that?

---

### Post by ianoshorty on 2008-03-17
Hate to bump this thread but im pretty desperate now :S

---

### Post by amk221 on 2008-05-12
My setup worked fine with screens of the same size, but now I have one widescreen and one standard, I get the same problem as you.

Plus my cursor can go off the edge of the screen which also makes X crash.
*(I know this can be fixed by setting Virtual in xorg - but because the conf file made by ati only has 1 entry for both screens I don't see how that works!)*

Have you had any luck with this?

---

