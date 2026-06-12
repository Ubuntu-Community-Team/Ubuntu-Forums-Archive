---
title: "How to make Grub play nice."
date: 2006-08-15
forum: General Help
---

### Post by chadwick359 on 2006-08-15
I have A SIIG PCI ATA card, and Whenever I plug a drive into it, Grub yells at me and gives me an Error 17 Code. Has anybody had any luck getting Grub to not hate PCI IDE cards?

---

### Post by zxee on 2006-08-15
I have a Promise Ultra100 TX2 and have never had any problems with it. I multiboot 7 distos now but have had many more.
Error code 17 is iirc filesystem not recognized. You may want to check your menu.lst and fstab entries.

Although it's at a gentoo forum there's a long thread here [http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)  that might provide more help.

---

### Post by chadwick359 on 2006-08-15
Well, I think I know what to do. I'm going to attempt to boot into a liveCD with the HDD connected and reconfigure grub from there. See if it takes.

---

### Post by infoseeker on 2006-08-15
I had a similar problem. This is my repaired menu.lst (appropriate section thereof):
> title           Ubuntu, kernel 2.6.15-26-686
root            (hd1,2)
kernel          /vmlinuz-2.6.15-26-686 root=/dev/hdc1 ro quiet splash
initrd          /initrd.img-2.6.15-26-686
savedefault
boot

Yesterday I uninstalled the 386 kernel, and after rebooting I too got the error.  The process somehow changed line 1 from (hd1,2) (boot partition) to (hd1,0) which is my root partition.
Any suggestions as to why?

PS. A few weeks back I created the boot partition and altered the setups, grub accordingly.  My boot partition used to be on hdc1 before I changed it.

This is my fstab file:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc                   proc    defaults        0 0

/dev/hdb        /media/cdrom0           udf,iso9660 user,noauto     0 0
/dev/hdc1       /                       ext3    defaults,errors=remount-ro 0 1
/dev/hdc2       none                    swap    sw              0 0
/dev/hdc3       /boot                   ext2    defaults,noatime        1 2


---

