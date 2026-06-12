---
title: "Can't boot from CD"
date: 2005-05-12
forum: General Help
---

### Post by matthew on 2005-05-12
This is a weird one...

I have both WinXP and Ubuntu installed on my laptop in a dual boot configuration using Grub. I can boot with either OS (multiple kernels available in Ubuntu) with no problems whatsoever. 

I just downloaded Knoppix 3.8.2 (yep, just came out on a sneak-peek at [http://distrowatch.com/?newsid=02640](http://distrowatch.com/?newsid=02640)) and wanted to play with it as I had been doing so for a while with 3.7 and 3.8.1. Long story short, I suddenly can't boot from a cd.

Tried earlier versions of Knoppix that I had booted from as recently as a few days ago. Nope.

Tried to boot from the Ubuntu live CD I haven't had time to play with. Nope.

Rebooted, entered my BIOS setup to check and confirmed that I had the cd-drive listed before the hard drive in the boot order. Yep. Changed them, saved it. Changed them back so the cd drive is listed first again. Saved it again. Still no cd-boot.

I can't think of any changes I have made recently that could/would cause this behavior. The cd drive works perfectly to read/write cd's and dvd's in both Linux and XP. I'm at a loss.

I can get the Grub prompt. Is there a way to boot from a cd in Grub?

Any ideas why I can't boot from cd at all and what else I might try?

TIA

---

### Post by poofyhairguy on 2005-05-12
Sounds like your BIOS is screeming for an upgrade.

---

### Post by tread on 2005-05-12
You haven't messed around with master/slave settings, have you? I think you cannot boot from a slave or something.

---

### Post by matthew on 2005-05-12
Hmm... I will see if I can upgrade the BIOS. I bought this laptop from CyberPower rather than a big-name company and have since discovered they aren't always on top of posting drivers/BIOS upgrades and so on on their web site.

The other poster had a good thought, but I haven't made any changes to the master/slave status.

---

