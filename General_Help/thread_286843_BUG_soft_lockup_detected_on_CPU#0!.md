---
title: "BUG: soft lockup detected on CPU#0!"
date: 2006-10-28
forum: General Help
---

### Post by makro on 2006-10-28
Centrino DUO 1.66 Ghz

I've tried to reboot for 10 times in a row... at the end edgy started when I switched on wireless light before boot... maybe this is only a coincidence...

Another strange thing is that sometimes boot hangs while fsck is working....

Linux 2.6.17-10-generic

---

### Post by dummies85 on 2006-11-15
same thing happened to me whie trying to boot with the generic kernel. Have you tried reporting this to launchpad?

---

### Post by mrunion on 2006-11-15
Same here -- locking up sometimes when fsck tries running or when trying to bring up network interfaces.  I also use a wireless card in an HP laptop.  Running kernel 2.6.17-10-generic (Uname also shows a #2 SMP after it in uname -a.)

Ideas?

---

### Post by timloco on 2006-12-05
I saw this error on my Compaq Evo n610C notebook when trying to boot up after a problem with the network driver (I think) it's the wlan200 - I'm using the orinoco_usb driver and randomly the keyboard stops working and the networking does also, until I reset.  I tried doing a hibernate instead of restart once and when I booted back up it showed this error and was hung until I power cycled.  Using Edgy...

---

