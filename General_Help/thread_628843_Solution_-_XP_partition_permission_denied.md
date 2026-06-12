---
title: "Solution - XP partition permission denied"
date: 2007-12-01
forum: General Help
---

### Post by lintoon on 2007-12-01
First things first,  I am not a linux expert so proceed with care.

I was getting "permission denied" error when trying to access my windows partition so I thought I should post my solution.  I had to edit my fstab and reboot.  This may not work for everyone but it may help someone.

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=da30f0b7-d4c3-43ac-b1b9-fc97edea3fb6 / ext3 defaults,errors=remount-ro 0 1
#/dev/hda1       /media/hda1     ntfs    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
# The line below was commented out by me
#UUID=B888951B8894D968 /media/Windows ntfs nls=utf8,umask=0222 0 0
#The line below was added by me
/dev/sda1 /media/Windows ntfs-3g defaults,force 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=6121d48f-e4b1-493f-a0d9-311e373fe7cd none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

------------
The problem was corrected by commenting out:
UUID=B888951B8894D968 /media/Windows ntfs nls=utf8,umask=0222 0 0

and replacing it with 
/dev/sda1 /media/Windows ntfs-3g defaults,force 0 0

I have added a couple of comments to my fstab to show the changes.
-----------

Note: The full path to fstab is  /etc/fstab
To edit it open terminal and type "sudo gedit /etc/fstab"

****** Important *****:
Before you edit fstab make a backup first
eg
Open terminal and type "cp /etc/fstab /etc/fstab.bak"
-----------

Also, you may have to ammend "/dev/sda1 /media/Windows ntfs-3g defaults,force 0 0" to match your system.
My Windows partition is mounted from /dev/sda1.  Yours may be different.

To find yours, open terminal and type "sudo fdisk -l"

Look for the line which has NTFS under the System heading.

Good luck.

---

