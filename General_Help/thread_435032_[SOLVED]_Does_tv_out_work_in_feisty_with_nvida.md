---
title: "[SOLVED] Does tv out work in feisty with nvida?"
date: 2007-05-06
forum: General Help
---

### Post by olavjunior on 2007-05-06
I remembered back when I installed edgy, I tried to connect a external display such as my tv or my projector. I had to accept the defeat, hoping that these problems would be solved in never versions of ubuntu. 

So is it??

---

### Post by Whiffle on 2007-05-06
Seems to.  I just opened up nvidia-settings, it saw my TV (composite out), I set it to twinview and it worked.

---

### Post by russell.h on 2007-05-06
I hauled my computer downstairs the other day and plugged it into my new TV (via the TV out on my geforce 6800GS), switched it on, and it booted just fine. Was limited to 1024x768, but I think that the fault of either my video card or the TV itself.

---

### Post by olavjunior on 2007-05-06
Sounds nice!

Anyone having tried with s-video?

I remember that the problem was that I had to save the chages to the xorg and reboot to get the tv to show, but to alter the xorg wasn't desireable.

---

### Post by Nythain on 2007-05-06
altering the xorg.conf isnt a big deal, as long as you take baby steps and remember to BACK UP a working copy... if it ever fails all you have to do from comand line would be sudo cp /path/to/backup/xorg.conf /etc/X11/xorg.conf

setting up anything visual/graphics related is usually gonna take modifying your xorg.conf

---

### Post by olavjunior on 2007-05-06
Yea, I know it's possible to alter the xorg, and if it just has to be done once it's ok. But as far as I understood, I had to alter it to extend my desktop, and then alter ig again when I deatached the tv... But I might be misunderstood, it's a long time ago..

---

### Post by olavjunior on 2007-05-10
Well, feisty is installed. The issue with having to alter the xorg to get seperate twin view is still present, but clone works fine, just set the resolution same for both monitors. 

RESOLVED

---

