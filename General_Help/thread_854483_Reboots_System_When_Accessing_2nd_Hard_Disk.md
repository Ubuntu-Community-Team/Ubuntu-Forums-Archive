---
title: "Reboots System When Accessing 2nd Hard Disk"
date: 2008-07-09
forum: General Help
---

### Post by rob150588 on 2008-07-09
Hi there. I'm pretty new to Linux (only been using it a week). Must say, it's absolutely brilliant. Anyway, that's not the point.

I have installed Ubuntu on a fresh hard disk (500gb WDC SATA), and I have two IDE disks (1no 80gd 1no 120gb) from the previous windows installation. I am trying to copy over all my documents, music & what-not onto the 500gb drive.

Ubuntu lets me access these drives for about 15 seconds...then just dies. The screen goes blank and the system reboots...:confused:

Does anyone know why this would happen ? And if so, how to stop it.

Cheers. Rob.

---

### Post by cmnorton on 2008-07-09
Please post your /etc/fstab. 

You should be able to upload it as an attachment in a reply, or you can edit the file -- it is read only -- and cut and paste the results here.

It sounds like something is not formatted correctly, but I have not a clue as to why it would reboot.

---

### Post by rob150588 on 2008-07-09
Here ya go...cheers for looking at this by the way...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0b0574e5-747d-40bc-9932-e659aae150b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6a518f2e-a271-41c2-941d-fccaaa5562b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

---

### Post by cmnorton on 2008-07-09
I do not see the second drive in fstab. If it's the same kind of disk, you'd make a mount point, probably in /media (as sudo*), and then add the necessary information to fstab (also as sudo). 

This line

/dev/sdb1         /mnt/sdb1         ext3     defaults,errors=remount-ro 0 1

is on one of our non-Ubuntu systems (Fedora 6). 

If this is a windows drive, you would change ext3 to the appropriate setting for a Windows file system, and there may be other things that have to be set as well.

If this second drive is intended as a Linux drive, then, as root (sudo) you would create a mount directory under /media as sudo. Using the fstab line above as an example, I created the /mnt/sdb1 directory. 

Then the line above (in /etc/fstab) causes the mount to occur at boot. However, you still have to run fdisk to create a partition table and fsck to format the drive with the ext3 file system, if this not a Windows drive.

Don't get overwhelmed by this. Take everything one step at a time. 

*
------------------------------------------
On Ubuntu systems, sudo is the preferred way to become root. If you user, for example fred, installed the system, then you would answer with fred's password when prompted by sudo.

---

### Post by rob150588 on 2008-07-09
Ah, you see. I assume the 2nd drive is not listed as I dare not click on it on the Places menu. Doing so will cause a total reset.

When you hover over it, it say "Mount Documents Drive" (Documents drive being the label I gave it in Windows). If I then click on it, it will let me access the contents of the drive, as I assume it automatically mounts it. But after about 15-30 seconds (usually nearer 15) it just reboots with no warning.:(

Just clicked on it and pasted the fstab data quickly...


[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0b0574e5-747d-40bc-9932-e659aae150b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6a518f2e-a271-41c2-941d-fccaaa5562b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0[/B]


...Don't know if that helps ?

---
Actually, that looks exactly the same as the first one I posted...sorry...

---

