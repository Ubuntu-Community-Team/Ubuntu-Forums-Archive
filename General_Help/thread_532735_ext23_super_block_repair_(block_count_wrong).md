---
title: "ext2/3 super block repair? (block count wrong)"
date: 2007-08-23
forum: General Help
---

### Post by ts70 on 2007-08-23
Hello, (new here)

I do have following difficulty:

(1) Hardware: Thinkpad T43 with a 120GB drive, otherwise standard
(2) disk layout: co-installation of WinXP, Win2000, OS/2Warp4(and its Bootmanager), Kubuntu Dapper and Ubuntu Edgy. The two Ubuntu partitions are out of disk order (i.e. /sda10 and /sda11, but physically between /sda7 (linux swap)  and /sda8 (fat32 data storage)).
Master boot manager is the graphics flavor of Grub, installed in MBR (stage 1) and on the edge-partition /sda11 (stage 1.5 and on)
(3) what happened: I changed the home Wifi from WEP to WPA after the last non-WPA-hardware is gone last week. Thus, I had to upgrade the OS/2 wifi driver (genmac). This crashed the OS/2 partition (/sda6) in a mysterious, but known way - only help is to recover the image. True Image under WinXP thinks it must "save the world from all evil" and changes partition types, partition order on disk etc. So, Grub ends in error 17 (menu.lst not found on the expected partition). Happily enough I have an old Suse10.0-DVD and can run the recovery system and fix the partition layout and types (with the help of fstab, which says who has to get what name). Fine. WinXP boots. OS/2 boots. Dapper boots. Edgy does not: 
(4) THE PROBLEM:
Edgy resides on /dev/sda11 physically between /dev/sda10 and /dev/sda8 on an ext3 file system. /boot/grub contains the "hot" grub data for booting all the different systems. This grub is modified (which took some work)to run the graphical interface as known from suse 10 etc. I do not want to change that.
Edgy starts booting, then discovers it should check the fs and the finds, that the Superblock has a 8 blocks bigger file system, than the actual partition size is. fsck refuses to fix anything about that.
What can I do to fix the superblock block count? Or the partition table? I guess, edgy was installed using the installers partitioner and I usually use Suse fdisk. I think, they have different thoughts about the disk geometry (i.e. how many heads and sectors give a cylinder) - so that might explain the 8 blocks difference (??). But how do I fix it?
Dapper (/dev/sda10) boots correct and mounts /sda11 without problems. Suse recovery also mounts the edgy partition without complaints (as long as I do not run fsck), so the fs is fine, only the block count needs to be fixed!

---

### Post by Herman on 2007-08-23
I think try resize2fs, (from a LiveCD), here is a link, [http://www.linuxcommand.org/man_pages/resize2fs8.html](http://www.linuxcommand.org/man_pages/resize2fs8.html)
Like,
```
resize2fs -p /dev/sda11
```Regards, Herman :)

---

### Post by ts70 on 2007-08-24
> **Herman said:**
> I think try resize2fs, (from a LiveCD), here is a link, [http://www.linuxcommand.org/man_pages/resize2fs8.html](http://www.linuxcommand.org/man_pages/resize2fs8.html)
Like,
```
resize2fs -p /dev/sda11
```Regards, Herman :)

Thanks a lot Herman!

It worked indeed (and was what I actually was thinking what should help: resize the FS to fit the partition.
Since there was a problem with the original situation I had to run it as

resize2fs -p -f /dev/sda11

Thanks a lot - everything runs just fine now.

TS

---

### Post by Herman on 2007-08-24
ts70, Hey!  
Thanks for the feedback, I'm happy it worked! Well done! Lucky you knew to use -f too!
Regards, Herman :)

---

