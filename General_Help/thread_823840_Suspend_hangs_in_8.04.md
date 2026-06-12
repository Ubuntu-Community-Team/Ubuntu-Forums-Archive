---
title: "Suspend hangs in 8.04"
date: 2008-06-09
forum: General Help
---

### Post by ygrignon on 2008-06-09
I switched from XP to Ubuntu 8.04 a few days ago and I haven't been able to get suspend to work.  I have an ASUS P4P800SE motherboard with an Intel P4, 1 Gb of ram and a Radeon 9550GE video card.

When I try to suspend, the computer hangs with the hd light on.  I have to cycle the power to reboot.  I logged the output of sleep.sh and it ends with "echo -n mem".  I checked kern.log and the last line before reboot is:
"[ 2874.186977] ACPI: PCI interrupt for device 0000:02:05.0 disabled".

I tried with linux 2.6.24-18 and -16 and get the same results.

Help pls.

---

### Post by Pjotr123 on 2008-06-09
This will be informative:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 4 )

---

### Post by ygrignon on 2008-06-12
Thanks Pjotr, it is informative but ... not the answer that I was hoping for :-(

---

