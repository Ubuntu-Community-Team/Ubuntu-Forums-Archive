---
title: "Cannot boot windows 10 after deleting ubuntu"
date: 2016-01-13
forum: General Help
---

### Post by diego53 on 2016-01-13
Dear forum members,

After having windows 10 and ubuntu dual booted on my laptop I decided I would no longer need Ubuntu.
Since I only installed it because I needed it in a course and I finished it.
So me and my ignorant mind delete the ubuntu partitions which resulted in a grub rescue.
A recovery usb does not seem to work (booting from it causes a blue screen) and using boot fixed changed the problem into a windows bootloader
with 0xc0000428 winload.exe problem.
Below are the pasebin links of the boot repair.
I hope that someone could help me, because it is my only laptop which I also need for projects.

With dear regards,
Diego Renting

[http://paste.ubuntu.com/14490645/](http://paste.ubuntu.com/14490645/)
[http://paste.ubuntu.com/14490484/](http://paste.ubuntu.com/14490484/)

---

### Post by oldfred on 2016-01-13
You may need to boot from sda1, not sda2 even though sda2 now shows all the necessary boot files. 
I might try moving boot flag to sda1 with gparted or your Windows repair disk (set active on command).

Where is /mapper coming from? Is this an Ultraboot with Intel SRT or caching to make boot faster. That may need a setting in BIOS/UEFI or be part of issue.

---

