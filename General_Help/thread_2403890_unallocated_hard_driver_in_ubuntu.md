---
title: "unallocated hard driver in ubuntu"
date: 2018-10-17
forum: General Help
---

### Post by nekkache on 2018-10-17
first 
when i start the computer .the system can t booting from the hard disk and typing in screen 
-------------------------------------------------------------------------------------------------------------------------------------
ALERT! UUID=dd84f4b3-d5bf-42e4-9b5e-ec685a461fad does not exist.   Dropping to a shell.
-----------------------------------------------------------------------------------------------------------------------------------


so i was starting it whit live cd 
but whene i typing the commend : sudo blkid or fdisk -l

 
---------------------------------------------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo blkid
/dev/sdb1: LABEL="UBUNTU 18_0" UUID="6056-C230" TYPE="vfat" PARTUUID="0027aa9a-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
---------------------------------------------------------------------------------------------------------------------------------------------------

so 
for that i was open gparted and i found this  **a **[B]big grey area saying something like Un Allocated.

how to restart my old system whit he s settengs and files !!![/B]

---

### Post by TheFu on 2018-10-17
If the disk can't be seen by the OS, then check the disk, sata cables, and disk controller.

sdb1 is the flash drive you used to boot, not the HDD, according to the data posted above.  There isn't any HDD recognized.

Does the BIOS see the disk?

Also, whenever posting commands and output, please, please, use **code tags**. This makes things line up and more readable.

---

