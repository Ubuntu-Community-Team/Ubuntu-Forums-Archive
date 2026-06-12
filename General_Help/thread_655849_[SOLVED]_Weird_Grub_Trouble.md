---
title: "[SOLVED] Weird Grub Trouble"
date: 2008-01-01
forum: General Help
---

### Post by think13 on 2008-01-01
I was running a dual-boot setup with Ubuntu Gutsy and Windows XP.  I had some boot trouble after installing IBM Rescue and Recovery, and I am now trying to restore Grub.

I read some how-to's for restoring grub.  They all say to run grub and then 'find /boot/grub/stage1'.  I always get Error 15: File not found.  I have also tried simply trying root (hd0,1) and then setup (hd0).  If I try this, I get Error 17: Cannot mount selected partition.

I even tried reinstalling Ubuntu.  I got hung up at 94% with the error 'grub-install (hd0) failed' 'fatal error'.

While trying some fixes, I found something else weird.
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5307    42626017    7  HPFS/NTFS
/dev/sda2            5308        6658    10851907+  93  Amoeba
/dev/sda3            6659        7168     4096575    b  W95 FAT32
/dev/sda4            7169        7296     1028160    5  Extended
/dev/sda5            7169        7296     1028128+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Notice that /dev/sda2 is of type 'Amoeba'.  It should be of type ext3.  The Ubuntu installer even says it is of type ext3.

Any Ideas?

---

### Post by p_quarles on 2008-01-01
When you ran grub, were you doing so from a boot disk, or from your current Linux installation? 

Have you tried using the [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")?

I'm just throwing those ideas out there. As far as I know, reinstalling Ubuntu should have fixed Grub, and I have never heard of the "Amoeba" filesystem. Wish I could offer more help, but the description of the problem has me scratching my head as well.

---

### Post by think13 on 2008-01-02
I ran grub from the Gutsy CD.

I have also tried Super Grub Disk.  I use the option to fix the grub installation, and it always fails, giving Error 17.  I have also tried other options on the disk, and they aren't helping.

---

### Post by pietjanjaap on 2008-01-02
If grub is working, if you can choose your ubuntu, then the problem is your hd nr's in your menu.lst.
Grub and live cd see hd numbers different, they can switch.
Boot with livecd then change menu.lst.
the first choice: example:

title		Ubuntu, kernel 2.6.20-16-generic
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Make more copies of this, so you have more choices when you boot, and change only de hd number hd0,0 hd0,1  hd0,2  hd1,0  hd1,1  etc
Find out witch one works, then change the menu.lst.

---

### Post by think13 on 2008-01-02
Grub isn't working. My computer is using the Microsoft XP bootloader at the moment.  I want to restore Grub as my bootloader, but all of my efforts have failed miserably. :(

---

### Post by jken146 on 2008-01-02
When you are trying to find /boot/grub/stage1, you need to be looking in your Ubuntu partition, not the /boot directory on the live CD.

---

### Post by think13 on 2008-01-03
So what would you recommend to do this?  There have been some restoring grub howtos that say to mount the ubuntu partition and chroot to it.  I still couldn't find the file after doing that, so I don't think that that is the problem.

---

### Post by think13 on 2008-01-04
I think the problem may stem from the fact that my partition is somehow using the 'Amoeba' filesystem, whatever the heck that is.  When using the Super Grub Disc, it listed that partition's type as 'Unknown', so it may not find the file because of that.  

When I tried reinstalling Ubuntu, it should have reformatted that partition as ext3, right?  So why is it still shown as type 'Amoeba'?

---

### Post by andymushu on 2008-01-04
I had a similar issue on my friend's laptop with installing the grub to a dualboot system. The hard drive had three partitions: the windows one, the factory installed recovery once standard on laptops, and the one i was trying to install ubuntu to. Here is how i fixed it: I booted to a live cd, opened up gparted under System --> Administration, then let it scan my drives. It came up with the three partitions, /media/sda1, /media/sda2, and /media/sda4, with sda4 being the partition i had created for installing ubuntu. After running through the whole ubuntu installer, at the final screen click on the advanced option. There should be an option for where to install the grub (forgive me if this isn't exact, it has been a while). Remembering what gparted had called the partition i was installing to, i subtracted 1 from the sdaX (in this case sda4) number (since computers number starting with 0). In my case I started with 4, so in the "install grub to:" box, i typed in "(0,3)", without the quotes. The first number is the hard drive, so if you were installing to a secondary hard drive, this number would become 1. The second number is the partition, which in my case was 3. After specifying this, it should install grub without a hitch. Good luck!

---

### Post by think13 on 2008-01-04
I solved the problem by formatting the drive as ext2, and then installing Ubuntu.  It worked without a hitch.  It probably wasn't that I formatted it as ext2, just that I formatted the drive.  After the format, fdisk gave the correct filesystem.

---

### Post by andymushu on 2008-01-04
good to hear that you got it figured out.

---

