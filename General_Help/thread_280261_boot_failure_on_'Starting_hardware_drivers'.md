---
title: "boot failure on 'Starting hardware drivers'"
date: 2006-10-19
forum: General Help
---

### Post by finite9 on 2006-10-19
A few weeks ago, my Acer Aspire 5021 laptop developed a problem booting, having been working fine for 7 months.  It would get to "starting hardware drivers" and hang there.  the hard disk would show constant activity for several seconds then stop.  I came no further.  I think it's PCMCIA that is loaded directly after this but I think the main problem is with the hardware drivers.

2 days ago, I decided to re-install it all with 6.06.1 amd64.  After re-installation, everything seemed fine...no more hanging.  But then I performed two activities simultaneously:  I installed all latest updates and installing the bcm43xx driver for my Broadcom wireless adapter, as instructed on the wiki (the manual way).

After reboot, same thing again: hanging on hardware drivers.  I am not sure it is becasue of recent updates that are incompatible with the bcm43xx driver or if it is the actual bcm43xx driver that is at fault, but I wonder if anyone can tell me where to look for errors!!!??  Do I look only in syslog for errors or is there another log that logs boot failures?

Does anyone else have this problem with recent updates and bcm43xx?

One thing that I think I may have done wrong is that when installing the bcm43xx driver, i do sudo apt-get install bcm43xx-fwcutter and I get the wl_apsta.o driver from the bcm43xx team and then do some funky command line thing to 'compile' it into the currently running kernel.  In the bcm43xx wiki it says to specify /lib/modules/ as the path to compile the driver into, but I had problems with that 1 year ago so ever since, I have compiled the driver directly into /lib/modules/2.6.15-25-amd64-k8.  Just in case this is causing the problem, I have now reinstalled again, performed all updates but NOT installed the bcm43xx driver.  All seems ok right now after just 2 reboots, but I am suspecting that if I follow the wiki and apt-get bcm43xx-fwcutter and install the wl_apsta.o driver then the same thing will happen again.

I am going to try installing the deb file driver instead of manually installing the wl_apsta.o driver...I noticed that there is a package on cafuegos site called bcm43xx-firmware.  Hopefully this may help, but I would appreciate any and all feedback on this issue.

---

### Post by stansaraczewski on 2006-12-12
I have the same problem - but don't know what I may have done to cause it.

---

### Post by finite9 on 2006-12-13
> **stansaraczewski said:**
> I have the same problem - but don't know what I may have done to cause it.

Well, unfortunately I cant remember how I fixed this, but I no longer use the apsta driver; I use the DEB file from Cafuegos web site instead, and I have a guide for it in my sig.  If a re-install helps without installing wireless drivers then try my guide to get wireless working.

---

### Post by stansaraczewski on 2006-12-13
I mis-spoke: not using wireless... and it doesn't always hang. Sporadic.

The mystery continues.

---

