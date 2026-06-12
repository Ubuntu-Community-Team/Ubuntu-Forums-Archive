---
title: "amarok xorg high cpu usage"
date: 2007-11-29
forum: General Help
---

### Post by DeFrancoj on 2007-11-29
Hi.

Running 7.10 on a Dell Dimension 8200 (2GHz, 1GB RAM, ATI RV350 GPU),

I have compiz enabled, using the open source ati drivers and AIGLX. The desktop cube is enabled. Now when I'm running amarok, and the window is open on the active face of the cube, xorg's CPU usage skyrockets. If I rotate the cube so some other face is facing me, it goes back down. 
Any idea why? I didn't think of amarok as a graphics intensive app...

Thanks all

---

### Post by SyL on 2007-12-19
Is amarok keeps updating the collection?
if so you can try the following

1/ turn off watch folder option
2/ delete ~/.kde/apps/share/amarok/collection.db
3/ turn on the watch folder option

amarok shouldn't burn the CPU anymore ...

---

### Post by DeFrancoj on 2007-12-19
Actually, amarokapp wasn't using much CPU; it was xorg. I turned off that equalizer visualization thing on the bottom, and that helped, but xorg still runs a bit high while drawing amarok.

---

### Post by andydread on 2008-05-02
I have this same problem with Hardy. 
ATI Radeon 9000.  turning off the analyser helped but its still sluggish.
In addition scrolling in Firefox 3b5 is slow and laggy.  
Videos on youtube are laggy with a slow refresh.

---

