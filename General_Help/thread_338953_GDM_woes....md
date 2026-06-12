---
title: "GDM woes..."
date: 2007-01-15
forum: General Help
---

### Post by d3d9 on 2007-01-15
Hi. This is my first post in this forum.

I've installed Ubuntu 6.10 on my machine, and am very satisfied with the performance. There is, however, this small problem: often, the GDM login window fails to appear on start-up, leaving me with a blank screen. Neither the [Ctrl]+[Alt]+[Backspace] nor the [Ctrl]+[Alt]+[Delete] key-combinations seem to work, and I am left with no other option but to hard-reboot the machine.

Is there any solution to this problem?

---

### Post by gwpritch on 2007-01-15
Sounds like a video card/driver problem. What video card do you have?  Are you able to log into X from the command line?

---

### Post by d3d9 on 2007-01-16
My video card gets detected as an 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device. Since my motherboard is a pretty old one, the card should be well supported. Besides, I've used Ubuntu Breezy & Dapper on my machine previously, without a hitch.

I'm unable to even access a bash prompt when this happens, so I don't know whether I can log on to X via the console or not. One more thing... I installed a few GDM login screens from art.gnome.org. Can those be the source of the problem?

---

### Post by gwpritch on 2007-01-16
I still thing it might be a video driver problem. Edgy may have a different version than Dapper. I had something similar happen when I tried to use the latest driver from ati for my video card. The only way I could get it to work was to downgrade to a previous version. 
Can you boot into recovery mode? If so you can try logging in to X from there. That might give you a better idea if its a problem with gdm or hardware/driver.
You might want to look for any error messages in /var/log/Xorg.0.log.  Also check /etc/X11/xorg.conf to see which driver you are using. I believe (but not 100% sure) that you should be using i810 driver. 
I'm no expert here, just going from seat-of-the-pants experience.

---

