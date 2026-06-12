---
title: "Grub error 13 help"
date: 2007-09-10
forum: General Help
---

### Post by Kpax1 on 2007-09-10
I have a dual boot Feisty and XP system. It is a new computer and I am initially configuring it. The problem is that I cannot boot an Operating System without having the Windows XP disk in at startup. Otherwise I get this error message:

Error 13: Invalid or unsupported executable format

Can anyone help with this?

---

### Post by Kpax1 on 2007-09-10
I got into recovery console, and ran the FIXBOOT command, but I still have the same problem. I get error 17: Cannot mount selected partition 
when trying to boot ubuntu

---

### Post by Kpax1 on 2007-09-10
I tried restoring Grub by booting into the live cd, opening a terminal, typing 'grub'. then:

sudo grub
root (hd0,1)
setup (hd0)
quit

However, when typing 'setup (hd0)' it says that the partition cannot be mounted!

---

### Post by Arwen on 2007-09-10
Is this sth helpful->[http://ubuntuforums.org/showthread.php?t=260625?](http://ubuntuforums.org/showthread.php?t=260625?)
Last time I had such error was when a blackout happened during partitioning when installing kubuntu so I had to start it all over(thank source it didn't kill my hd!)

---

### Post by logos34 on 2007-09-10
From the live cd run

**sudo fdisk -l** (lowercase L)

You could try running **fixmbr** command from the xp recovery console, see if it allows you to get into windows without needing the xp cd.  But you should be able to use grub.  Did you just install ubuntu?

Can you post /boot/grub/menu.lst too? (click on your root partition to mount first)   Maybe the path is wrong

ADD: here's [error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17").  Check the Bios like it says

---

### Post by Kpax1 on 2007-09-11
I ran 
sudo fdisk -l

> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

 Device          Boot               Start               End                             Blocks              Id                System
/dev/sda1            *                 1                  1216                     9767488+             83               Linux
/dev/sda2                            1217              30401                234428512+            5                 Extended
/dev/sda5                           1217                13374                 97659103+            83                 Linux
/dev/sda6                           26755              30401                29294496                82  Linux swap /Solaris

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280

 Device         Boot             Start                    End                   Blocks                 Id                    System
/dev/hda1         *                1                       1275                10241406             7                  HPFS/NTFS
/dev/hda2                         1276                 10010                70163887+        f           W95 Ext'd (LBA)
/dev/hda5                          1276                10010              70163856             e         W95 FAT16 (LBA)



---

### Post by Kpax1 on 2007-09-11
menu.lst

> 
title		Ubuntu, kernel 2.6.20-16-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b52b5f0a-8c81-4bc9-938d-f72643b27294 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b52b5f0a-8c81-4bc9-938d-f72643b27294 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic 

title		Ubuntu, kernel 2.6.20-15-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b52b5f0a-8c81-4bc9-938d-f72643b27294 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b52b5f0a-8c81-4bc9-938d-f72643b27294 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic 

title		Ubuntu, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/hda1 
title		Microsoft Windows XP Home Edition 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


---

### Post by logos34 on 2007-09-11
> **Kpax1 said:**
> I tried restoring Grub by booting into the live cd, opening a terminal, typing 'grub'. then:

sudo grub
root (hd0,1)
setup (hd0)
quit

However, when typing 'setup (hd0)' it says that the partition cannot be mounted!

According to your fdisk, your linux root is the first partition on the second disk (sda)--you should have typed 'root (hd**1,0**)'.  Using 'find /boot/grub/stage1' would have avoided this error.

But the disk boot order appears to have been switched in the bios, so go back and make sure hda is first, then run the command again:

> sudo grub
find /boot/grub/stage1
(should output 'root (hd1,0)'--enter this in next command)
root (hd1,0)
setup (hd0) -->this should srite grub to mbr of hda
quit

Try substituting '**rootnoverify**' for 'root' in the windows menu.lst entry.

---

### Post by Kpax1 on 2007-09-12
I did everything exactly as you explained it and it solved my problem.

Thanks logos34

---

