---
title: "USB HD being used with many machines?"
date: 2006-07-12
forum: General Help
---

### Post by rebelfallen on 2006-07-12
I have a question that is sort of simple, and yet not simple at all at the same time. ](*,) 

I bought a maxtor 100gb USB hard drive yesterday. I installed Ubuntu successfully on it. I dual boot Fedora Core 5, and Dapper on my home machine. FC5 is on my internal drive. All is well.

I brought my drive over to another computer that uses WinXP. I plugged it in, and changed my bios to boot the USB first. When it loads it gives me Grub and I select the option I want. Then when it starts to boot it shows mounting errors and only lets me use busybox. I have no idea why. 

I change the bios to boot my SATA first, Windows loads no problem. Why am I having issues with this USB drive now when it works perfectly fine at home? Do I need to edit my grub, or mount something new or what is going on? I thought it would just be a plug and play situation since this is a totally separate hard drive.

Thanks!

---

### Post by rebelfallen on 2006-07-12
Update: I get grub up, and "e" the kernel I want to use. I then edit the kernel line trying different partitions "/dev/sda1" to "/dev/sda5" and no such luck. The errors are:

Mounting root file system
Mount: mounting on /dev/sda1 on /root failed: no such device
/bin/sh: can't access tty; job control turned off


So bios is not recognizing /sda I suppose. How do I find out what the system is calling my USB device?

---

### Post by DaveRowell on 2006-07-13
To access your drive information:
Right-click 'My Computer' on the 'Start Menu'
Select 'Disk Management' from the left side of 'Computer Management'

The graphical display will give you the disk order and partition order

---

