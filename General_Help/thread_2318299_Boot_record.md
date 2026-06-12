---
title: "Boot record"
date: 2016-03-24
forum: General Help
---

### Post by Curbie on 2016-03-24
Does Xubuntu setup it's boot record with grub, or something else? I tried to get into the grub menu with sudo grub after booting the install disk, but that returned a command does not exit message, or the like.

Does Xubuntu setup it's boot record on the drive outside a partition, or within a chosen partition?
 

Also, is there a command to switch from 512 read/writes to 4096 read/writes once sector boundaries are straightened out?[
 

Curbie

---

### Post by Bucky Ball on 2016-03-24
*Thread moved to **General Help**.*

---

### Post by Dennis N on 2016-03-25
You may wish to clarify what you mean by "boot record", but the grub menu entries are from /boot/grub/grub.cfg. That file is created and updated by scripts in /etc/grub.d which run whenever you or the system runs the command update-grub. Each OS has a grub.cfg file in it's own file system, but in a BIOS system the one used for the menu that you see is from the OS the MBR (Master Boot Record) points to.

On the block size, I can't give you an answer.

---

### Post by oldfred on 2016-03-25
How BIOS based systems boot from MBR and Windows then from PBR. Grub does not use PBR, normally.
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) 

This is all standard now.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by Curbie on 2016-03-25
Dennis N, Thanks for the reply, your query on clarifying what I mean by "boot record", got me thinking about just what did I mean by "boot record" MBR or PBR??? After reading OldFred's link on multibooters, it seems that the BIOS always looks on sector/block zero for the starting link to the bootloader (which makes sense), I'm hoping that that Xubuntu installation always creates a PBR that the MBR links to, because that could explain why after manually shifting the partition to correct boundary errors, the test drive will no longer boot???

So maybe the running command update-grub after the partition shift, will correct the booting issue.

I'll give this plan a try.

Curbie

---

### Post by sudodus on 2016-03-26
If you move the head end of a partition, the bootloader will not find it. What you can do is repair/re-install the grub bootloader with ***grub-install***. (***update-grub*** will not do it for the system that the bootloader points to, but for the other systems in a multi-boot system.)

See the following link: [Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

particularly the paragraphs about reinstalling and fixing a broken system.

You can also try the automatic methods of [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

