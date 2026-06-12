---
title: "Error Mounting Volume"
date: 2013-04-18
forum: General Help
---

### Post by cherismaticanas on 2013-04-18
Hello,

I'm a little bit new to ubuntu and I just installed Ububtu 13.04 on my laptop . I have 3  harddrives, 2 of them are working great. the last one isn't. 

If I go to places and select , I get this:

Unable to access “105 GB Volume”

Error mounting /dev/sda2 at /media/ubuntu/8AB0F007B0EFF799: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/8AB0F007B0EFF799"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


If someone could help me, it would be great.

Anas Mohammed

---

### Post by AmbiguousOutlier on 2013-04-18
Hello, and welcome to the forums, firstly what's the output of;

fdisk -l
nano /etc/fstab

---

### Post by cherismaticanas on 2013-04-18
Nothing has showed for the command fdisk -l

for the next command nano /etc/fstab

overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

(I'm actually using the live cd and trying without installation now)

---

### Post by AmbiguousOutlier on 2013-04-18
try;

sudo fdisk -l

I take it this is a Windows machine with 3 physical HDD or does windows see 3 partitions on 1 or 2 disks?

---

### Post by steeldriver on 2013-04-18
Assuming sda2 is a Windows system volume, have you tried doing exactly what the error message tells you? i.e. booting into **Windows **and fully shutting it down?

[http://ubuntu.windows8az.com/185928-unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://ubuntu.windows8az.com/185928-unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by cherismaticanas on 2013-04-18
Sudo fdisk -l  Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x878c7c70     Device Boot      Start         End      Blocks   Id  System /dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT /dev/sda2   *      206848   205006847   102400000    7  HPFS/NTFS/exFAT /dev/sda3       205006848   329299967    62146560   83  Linux /dev/sda4       329299968   625141759   147920896   83  Linux  Disk /dev/sdb: 1001 MB, 1001848320 bytes 32 heads, 63 sectors/track, 970 cylinders, total 1956735 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x4d025b49     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *          63     1955519      977728+   b  W95 FAT32  

it is a windows machine but after installing ubuntu something went wrong and i couldn't go back to windows . 
 I'm using ubuntu via usb . when i reboot without this usb , system shows "Operating system not found" I tried to restore using my windows 8 installation disk , but it is not reading . 
I'm totally stucked with this Operating system not found message .

---

