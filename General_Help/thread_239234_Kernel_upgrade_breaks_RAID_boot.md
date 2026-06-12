---
title: "Kernel upgrade breaks RAID boot"
date: 2006-08-18
forum: General Help
---

### Post by Cheakamus on 2006-08-18
I am running Dapper Drake with a RAID 1 partition (/dev/md0) as my root filesystem. Every time the kernel is upgraded it rewrites /boot/grub/menu.lst and changes the root filesystem to /dev/hda1. With my next reboot it hangs the system, since hda1 is busy in md0. I can edit the kernel parameters in the grub boot menu to get it right, then edit /boot/grub/menu.lst to fix it, but that's a pain in the butt for every kernel upgrade.

So, my question is how do I force the kernel upgrade to use the **correct** root filesystem (/dev/md0 and not /dev/hda1) when it rewrites /boot/grub/menu.lst?

Thanks!

Jay

---

### Post by HAARP on 2006-08-19
There's some stuff commented out in the menu.lst. You'd think there's no attention paid to that, but actually, it gets used everytime update-grub is invoked. Change the path in the commented-out-part of the menu.lst to your RAID, and it should work.

btw. how did you get your system to boot from RAID which is root? I tried doing this with a RAID0, but I had no luck.

---

### Post by Cheakamus on 2006-09-16
Thanks. It turns out the kopt setting was the ticket.

I don't think it will work with RAID0. I'm using RAID1.

---

### Post by HAARP on 2006-09-16
That post is quite old. I managed to do it by now ;)

---

