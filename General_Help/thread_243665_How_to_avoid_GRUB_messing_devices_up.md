---
title: "How to avoid GRUB messing devices up?"
date: 2006-08-25
forum: General Help
---

### Post by tama on 2006-08-25
Hi, this is my first post here. Actually I'm quite new to Ubuntu and Linux, but I'm loving to face and solve all the trouble it's getting me :p.

The thing is that I've recently installed Ubuntu in my brother's computer and I have problems with GRUB. The computer has a SATA disk and an IDE disk.

I have Ubuntu installed in the SATA and Windows in the IDE. GRUB is installed in the MBR of the SATA and the boot sequence is CD, SATA, IDE.

Then, when it boots, GRUB takes hd0 as the SATA and hd1 as the IDE. Good so far. But device.map says:
```
(hd0)   /dev/hda
(hd1)   /dev/sda

```
That is, all the way around :confused:.

So when update-grub is called (in a kernel update for instance) menu.lst is messed up. Now Ubuntu is supposed to boot from hd1, but when it tries to boot, GRUB doesn't find the kernel, of course. It is in hd0 ](*,)!!!

Then I have to manually boot and change hd1 by hd0 in menu.lst for it to work again, but when I'm gone, my brother will have no computer!!

I tried to manually edit devices.map and run update-grub, but nothing, it keeps thinking that the SATA is hd1.

Hope that someone can give advice...
Thanks!

---

### Post by Ocxic on 2006-08-25
in your menu.lst there is this option:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0) <---change this line, do not uncomment the line.

change the default to "(hd1,0)" then run sudo update grub, check you menu.lst, and you should have no more problems.

---

### Post by tama on 2006-08-25
That worked!!

I thought it had sth to do with auto-detection of devices or whatever...

Thanks!!!

---

