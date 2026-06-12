---
title: "Grub error 17"
date: 2007-05-20
forum: General Help
---

### Post by wolf_man on 2007-05-20
I receive Grub error 17 when booting my laptop. I have 2 OS's on my machine, XP and Ubuntu. Before this error i was migrating data off of the XP partition to permanently remove XP. I deleted the secondary partition on the hard drive, which was an NTFS partition used solely for storing data. After i removed the partition i could not boot. Below is how i have my hard drive set up

[SIZE="3"]ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           12749       13607     6899917+  83  Linux
/dev/sda3           14339       14410      578340    5  Extended
/dev/sda4   *        6375       12485    49086607+  83  Linux
/dev/sda5           14339       14410      578308+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$[/SIZE]

My menu.lst is the folowing;
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
6

I am guessing i need to reinstall the GRUB loader, but how?

---

### Post by vtel57 on 2007-05-20
Your menu.lst has the wrong partition assignments for your Ubuntu / (root) partition. According to your info above, your Ubuntu / (root) is located on partition sda2, which should be assigned as (hd0,1) in your menu.lst. Edit your menu.lst to correct this. Don't forget to edit the root entries also. They are currently sda3, but should be sda2. 

When you removed that one partition, the remaining partitions got assigned new designations. I think this is what screwed things up for you.

Luck!

---

### Post by mbradlcu on 2007-05-20
as mentioned in the above post,, you can try these settings on the fly by editing at the grub prompt,, hit the "Esc" key, then "e" for edit,, make your changes and hit "Enter" then "b" to boot.. have fun!

---

