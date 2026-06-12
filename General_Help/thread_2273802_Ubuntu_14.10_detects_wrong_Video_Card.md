---
title: "Ubuntu 14.10 detects wrong Video Card"
date: 2015-04-15
forum: General Help
---

### Post by zeroo on 2015-04-15
On my Ubuntu 14.10 I have been noticing sluggishness on graphical applications.  When opening a folder my computer seems to stall and even when typing there is some pauses here and there.  Sometimes the stalls are even for upwards to 20 seconds.   

I'm using a decent computer and not running anything particularly stressful so I've been poking around to see what the issue is. 

When I run "lspci -vnn | grep VGA -A 12" it tell me my video cards is a [COLOR="#FF0000"]Radeon HD 7850[/COLOR].  The problem is that the video card that I actually have is an [COLOR="#FF0000"]ATI R7 265[/COLOR].  


I tried installing the correct drivers from the ATI website but the drivers did not work properly.  Is there anything I can do?

---

### Post by Vladlenin5000 on 2015-04-15
> **zeroo said:**
> When I run "lspci -vnn | grep VGA -A 12" it tell me my video cards is a [COLOR=#FF0000]Radeon HD 7850[/COLOR].  The problem is that the video card that I actually have is an [COLOR=#FF0000]ATI R7 265[/COLOR].  

Same thing.

> I tried installing the correct drivers from the ATI website but the drivers did not work properly.  Is there anything I can do?

Don't do that... Go to System Settings > Software & Updates and, in the rightmost tab you'll find additional (proprietary) drivers offered. Choose the recommended one, allow time for it to download and install. Reboot. Done!

---

### Post by zeroo on 2015-04-15
Ah, my mistake.  I realized they were the same a bit after posting by googling the two.  

I installed the additional proprietary drivers offered and rebooted but still experienced some lag.  After poking around some more I found there was a bug with Cinnamon-Desktop (which I'm using) and having Vsync enabled in Catalyst.  I disabled Vsync and everything seems to be working well now.  

Thanks!

---

### Post by Vladlenin5000 on 2015-04-15
You're welcome. :p
Glad it's working as designed/intended now.

---

