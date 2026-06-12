---
title: "Freezing half way through boot up, after local-premount"
date: 2007-06-08
forum: General Help
---

### Post by jubalj on 2007-06-08
Hi guys,

my ubuntu had been working well previously, even the upgrade from 6.06 to 7.04 went reasonable well.

But now I cant seem to boot ubuntu, even in recovery mode..

this is my grub line
root (hd2,0)
kernel /boot/vmlinuz-2.6.20-15-386 root=/dev/sdb1 ro single
initrd /boot/initrd.img-2.6.20.15-386

the only recent change that i can remember making to the system was changing UUID device name to /dev/sdb1 for root as it wasnt working with UUID number. And im pretty sure it was working fine after i changed it to /dev/sdb1

Find attached a screen shot of where exactly it freezes.. in recovery mode, with additional options of noapic, apci=off.

I am using a core2duo 6600 with Asus p5n32 SLI SE latest firmware. 2G of RAM. /boot (ext) partition is on ide drive, and the root partition is on a SATA driver (ext3?)

Would really appreciate any tips on what I could do work out whats wrong.

Thanks
Jubal

---

### Post by logos34 on 2007-06-09
> this is my grub line
root (hd2,0)
kernel /boot/vmlinuz-2.6.20-15-386 root=/dev/sdb1 ro single
initrd /boot/**initrd.img-2.6.20.15-386**

Shouldn't there be a dash between the 20 and 15:

**initrd.img-2.6.20-15-386**

?

If so Grub can't find the file.

That's how the initrd images are listed on my edgy and feisty kernels.

---

### Post by jubalj on 2007-06-10
I just checked my menu.lst, it's actually a typo on my part, the grub entry does have the hyphens\ at the correct location.

Presumably  if it cant find my kernel, initrd, root partition.. I should get some sort of error message?

---

