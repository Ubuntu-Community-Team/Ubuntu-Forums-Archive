---
title: "Replace Windows Boot Loader with GRUB"
date: 2007-09-20
forum: General Help
---

### Post by Merritt.kr on 2007-09-20
Situation: Installed Kubuntu. Installed Vista. Want Vista gone for HDD space. Computer boots using Windows Boot Loader, before Grub kicks in.

I imagine if I am remove windows, I should kick out windows boot loader and use grub all the way, and it would improve my boot time as well. How can I safely go about this? I've looked and looked, but so far only finding things about removing grub or ubuntu, not the other way around!

Thanks in advance for any help or suggestions!

---

### Post by jnorthr on 2007-09-20
You can just use fdisk to toast your vista partition, assuming you've made backups of everything you need. You will need to replace your bootloader anyway, if you choose grub for this, it will give you the choice of which o/s to boot, and of course if there is no vista, there i no choice, if you see what i mean.

You may want to burn a copy of supergrub as an .iso CD data disk first before loosing vista. Then try rebooting into the supergrub CD to test it out and make sure it does what you want, and works as you expect. When you are happy with that, then toast vista from within kubuntu using fdisk.

---

### Post by Merritt.kr on 2007-09-21
Alright, so, what, just "sudo grub install", or something to put it in the MBR, and all should boot fine?

---

