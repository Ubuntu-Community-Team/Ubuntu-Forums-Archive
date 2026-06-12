---
title: "problem with monitor/video card"
date: 2007-12-01
forum: General Help
---

### Post by Emperor.Travis on 2007-12-01
Alright, here's the problem. 
 I just installed Ubuntu on a dual boot machine with Windows Xp. Windows boots just fine so I'm not worried about that. 
 But every time I try to boot into Ubuntu it goes through the little scrolling bar to show you it's loading and then it says "loading" in little letters in the upper left of the screen. What happens next is the monitor goes black and the row of little green lights below the screen flash, all in unison. After a second of that the flashing stops and the power light goes orange. From there the only thing I can do is hard reboot it. 
 Here's my computer's specs, Intel Pentium 4 2.4 Ghz, 1 gig of ram, and my video card is a Nvidia GeForce 7600 GS. 
 Anyone know what the problem is and a fix for it?

---

### Post by -grubby on 2007-12-01
open up the Ubuntu "recovery" after restarting. then type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 

run through that and either select the "nv" or "nvidia" driver if none, select "vesa"

---

### Post by Emperor.Travis on 2007-12-01
Alright it worked! Thanks a lot. Now I've just got to remember what I set my password as.

---

