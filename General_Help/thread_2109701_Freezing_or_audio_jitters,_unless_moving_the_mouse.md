---
title: "Freezing or audio jitters, unless moving the mouse."
date: 2013-01-28
forum: General Help
---

### Post by grey1beard on 2013-01-28
Since I did a fresh install of 12.04LTS and after a couple of upgrades, I, too, have found that my Toshiba laptop Celeron 2.6Ghz, 32bit running the 3.2.0-36 kernel would only keep running if I moved the mouse at frequent intervals. Some freezes could be restarted by the enter key or even a quick poke of the power button, and I could only boot up using the recovery mode version.
Finding the following on the Thread **"10.10 hangs unless typing or moving cursor"**, #22 -
> 
I had to use the workaround suggested by sfranzyshen to fix booting of Ubuntu 11.04 on a Toshiba nb300 netbook.
The kernel is Linux 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux.
So, in /etc/default/grub I set
Code:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"**
and then run
Code:
**sudo update-grub**
and restart.

I tried this, an it has worked perfectly since. It now boots OK, and I have just installed a webcam plus software, and all is still working perfectly.:D

John

---

