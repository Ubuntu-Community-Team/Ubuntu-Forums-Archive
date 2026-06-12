---
title: "Can't (dual)boot Windows XP. No problem with GRUB. Please Help!"
date: 2007-09-05
forum: General Help
---

### Post by Jungleboss on 2007-09-05
My very irritating problem is the following. I have two SATA disks. The primary has Windows XP on it (installed before Ubuntu; actually ghosted). Ubuntu is residing on the secondary disk, GRUB is also there. Ubuntu always boots fine! But if I have booted Ubuntu and reboots and selects XP in GRUB menu Windows begins to load but I get a blue screen a couple of seconds later.

The troublesome workaround, I have found out, is unplugging the Ubuntu disk from the motherboard. Then XP boots fine!

I can plugin the Ubuntu disk when Windows has booted once. No problem to boot XP after that with both disks. But if I load Ubuntu I'm stuck again, and must follow the same procedure as described above (unplug the Ubuntu disk...) to be able to boot XP.

I think this can have something to do with my SATA controller using AHCI, but I'm not sure.

It's as if Ubuntu changes some hidden parameter regarding the disks and thus XP crashes. I don't get it. Even if I don't mount any partitions, on the Windows disk, in Ubuntu XP can't be started without the workaround.

Please help!

---

### Post by tech9 on 2007-09-05
It sounds like a hardware conflict to me...

check out this link for more on lilo and grub dual booting...
[http://www.ibm.com/developerworks/linux/library/l-bootload.html](http://www.ibm.com/developerworks/linux/library/l-bootload.html)

---

### Post by Jungleboss on 2007-09-06
You can be right about the conflicting hardware, but I don't think it as something to do with the boot loader. I get the same blue screen if using Windows boot loader also.

I also have updated my bios and sata drivers for Windows, but still the same problem.

I also have tried not to mount any of the Windows NTFS partitions in Ubuntu. But it's as if the mere boot into Ubuntu is sufficient to get the the loading of XP to crash.

---

