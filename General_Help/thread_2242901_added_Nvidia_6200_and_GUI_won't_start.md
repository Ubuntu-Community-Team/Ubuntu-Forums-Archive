---
title: "added Nvidia 6200 and GUI won't start"
date: 2014-09-04
forum: General Help
---

### Post by michael212 on 2014-09-04
Somewhat new to this, I have experience with Linux but not well versed in troubleshooting the config and gui settings.  Dual booting XP with Ubuntu 14.04 on my older Dell B110 desktop, Celeron 2.5 GHz, 2gb ram, it was working fine until I added an Nvidia GeForce 6200 256mb PCI card.  Previously was using the onboard Intel video.  The video card works great in Windows XP.  After adding the card, Ubuntu starts loading (shows the "Ubuntu" splash) then crashes to the console with streams of "corrupted low memory" until it just locks up completely and I have to power cycle.  Even tried to boot the Ubuntu DVD to reinstall the OS, and the system crashes soon after the splash screen.  Won't load Xubuntu off DVD either.  But if I remove the Nvidia card and go back to onboard video, it will load with no issue. 

I have been searching/digging into a lot of the Nvidia driver issues but I'm not having any luck.  I think I may have made it worse.  At one point I had gotten into the recovery mode and had the desktop running--I believe it was with the Nouveau drivers.  Unfortunately, I tried to update with the downloaded Nvidia driver and now I can't get past the "low performance graphics mode" screen.

Can someone help me figure out what to do next? How can I see what driver Linux is trying to use, and how can I configure it back to the Nouveau driver? 

Should I be concerned that I can't even run a DVD boot copy of Ubuntu with this new video card? 

Thanks for any help,
-Michael

---

### Post by deadflowr on 2014-09-04
Perhaps you need to add nomodeset
Looky here
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

and here
[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by michael212 on 2014-09-05
Thank you! That did the trick to get the CD booting again.  I also tried on my hdd installed version, but I think I had screwed the drivers up too much on that (just got stuck on the "low video or reconfigure" menu again).  So I reinstalled it just to start over.  It boots and runs now, but I'm not sure it's even using the Nouveau driver.  It's stuck in some odd resolution and painfully slow (see the dialog boxes redraw as it opens/closes).  How can I figure out if Nouveau is loaded? Or should I try again installing the Nvidia downloaded driver?

---

