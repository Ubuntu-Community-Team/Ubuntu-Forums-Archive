---
title: "Flash Drive Help!"
date: 2007-01-23
forum: General Help
---

### Post by CCBalla10 on 2007-01-23
Hey guys got a huge problem.  When I plug in my USB flash drive, it automounts and shows a usbdisk on my desktop.  But when I try to eject the usbdisk i get an error saying 
"Error: mount point /home/austin/Desktop is not below /media/
eject: unmount of `/home/austin/Desktop' failed"  Also on my desktop I have a file named "devices" and 4 folders titled "004" "003" "002" "001" and all of these are locked.  Also all my files I had on my desktop are gone... someone please help me!

---

### Post by CCBalla10 on 2007-01-23
> **CCBalla10 said:**
> Hey guys got a huge problem.  When I plug in my USB flash drive, it automounts and shows a usbdisk on my desktop.  But when I try to eject the usbdisk i get an error saying 
"Error: mount point /home/austin/Desktop is not below /media/
eject: unmount of `/home/austin/Desktop' failed"  Also on my desktop I have a file named "devices" and 4 folders titled "004" "003" "002" "001" and all of these are locked.  Also all my files I had on my desktop are gone... someone please help me!

NEVER MIND!!!! I fixed it by simply typing this into the terminal...

austin@myUbuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        7295    48355650    5  Extended
/dev/hda5            1276        7257    48050383+  83  Linux
/dev/hda6            7258        7295      305203+  82  Linux swap / Solaris

Disk /dev/sda: 262 MB, 262406144 bytes
16 heads, 32 sectors/track, 1001 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1001      256240    6  FAT16
austin@myUbuntu:~$ sudo mount /dev/sda1 /media
austin@myUbuntu:~$ 


**NOW MY FLASH DRIVE WORKS AGAIN!**

---

