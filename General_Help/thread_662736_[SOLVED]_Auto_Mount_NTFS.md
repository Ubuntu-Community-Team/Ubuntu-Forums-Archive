---
title: "[SOLVED] Auto Mount NTFS"
date: 2008-01-09
forum: General Help
---

### Post by diwas on 2008-01-09
I have windows' 3 partitions all having NTFS file system. But when they were FAT32, Ubuntu used to auto mount them on system startup. So I want the partitions to mount automatically during the system startup. So is there any way out?
Thank you.

---

### Post by malfist on 2008-01-09
They should do that anyway. Check and make sure they are in your fstab file.

---

### Post by ARhere on 2008-01-09
You did not give enough information, as the NTFS partitions _will_ auto mount if all is good.

What error, if any, are you getting?  What happens when you manually mount it?

-AR

---

### Post by diwas on 2008-01-09
When i manually mount it, it asks for the system password(root password). Thats it nothing else. And how would i know if they are present in fstab??

---

### Post by diwas on 2008-01-09
here is my fstab. sda1 sda5 and sda8 are NTFS.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=a2376e69-13d5-47fb-a3c4-a95ef314ec20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5085-C202  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=283C-11F2  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=474A-F9A1  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=2b88b156-d53a-4686-9581-61fb64589d45 none            swap    sw              0       0
# /dev/sda7
UUID=c5060c1d-f29b-4412-b672-1e899dd55777 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by cdaringe on 2008-01-09
this might be a silly question,
but do you have ntfs-3g installed?

---

### Post by diwas on 2008-01-09
Yes it is installed.

---

### Post by PRC on 2008-01-09
> **diwas said:**
> here is my fstab. sda1 sda5 and sda8 are NTFS.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=a2376e69-13d5-47fb-a3c4-a95ef314ec20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5085-C202  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=283C-11F2  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=474A-F9A1  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=2b88b156-d53a-4686-9581-61fb64589d45 none            swap    sw              0       0
# /dev/sda7
UUID=c5060c1d-f29b-4412-b672-1e899dd55777 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Please feel free to ignore me as I know stuff all, but if sda1 sda5 and sda8 are ntfs will they work in the above lines when they are declared as vfat ?

Paul c

---

### Post by Craigus on 2008-01-09
I think PRC has nailed it here.

Your fstab still has the vfat settings from when the partitions were fat32. You want:


```
# /dev/sda1
UUID=5085-C202 /media/sda1 ntfs-3g defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=283C-11F2 /media/sda5 ntfs-3g defaults,utf8,umask=007,gid=46 0 1
# /dev/sda8
UUID=474A-F9A1 /media/sda8 ntfs-3g defaults,utf8,umask=007,gid=46 0 1
```

Assuming that the UUID's are correct.

---

### Post by diwas on 2008-01-10
Oh...so thats the problem! I will try these codes.

---

### Post by diwas on 2008-01-11
I replaced my fstab with what you have posted, but still the drives did not mount automatically. Yet there are no error messages. Any suggestions?

---

### Post by danwood76 on 2008-01-11
with the fstab changed does sudo mount -a give you errors?

regards,
Danny

---

### Post by diwas on 2008-01-11
Yes, the errors are:
Failed to access '/dev/disk/by-uuid/5085-C202': No such file or directory
Failed to access '/dev/disk/by-uuid/283C-11F2': No such file or directory
Failed to access '/dev/disk/by-uuid/474A-F9A1': No such file or directory

---

### Post by danwood76 on 2008-01-11
The UUIDs must be different.

Replace that section with this:

# UUID=5085-C202/dev/sda1
/dev/sda1 /media/sda1 ntfs-3g defaults,utf8,umask=007,gid=46 0 1
# UUID=283C-11F2
/dev/sda5 /media/sda5 ntfs-3g defaults,utf8,umask=007,gid=46 0 1
# UUID=474A-F9A1
/dev/sda8 /media/sda8 ntfs-3g defaults,utf8,umask=007,gid=46 0 1

and try running that sudo mount -a again.
if you get errors again can you post sudo fdisk -l

regards,
Danny

---

### Post by diwas on 2008-01-12
There were no error message this time. I should reboot my system and check whether that worked.
Anyways in the meantime can you please tell me what does 
sudo mount -a 
stand for?
Thank you.
Diwas

---

### Post by danwood76 on 2008-01-12
that command mounts all the lines in your fstab like when you boot up, you can use mount to mount individual partitions but the -a switch tells it to look in the fstab.

Do the drives apepar on your desktop when you reebot?
And if not can you access them through /media/sda*?

regards,
Danny

---

### Post by diwas on 2008-01-13
No all the drives appeared when i corrected the fstab and inserted sudo mount -a in the terminal. Well let me boot into ubuntu and i wil inform you for the sucess(hopefully)

---

### Post by diwas on 2008-01-13
....And voila! It works!!! thank you so much for the solution...!!!! And for the guide to a new syntax: sudo mount -a
Thank you again!

---

