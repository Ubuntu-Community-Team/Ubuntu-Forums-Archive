---
title: "[SOLVED] how do I set ubuntu to run a terminal command on startup?"
date: 2008-06-05
forum: General Help
---

### Post by tippx on 2008-06-05
so my windows partition will not mount unless i open it in nautilus with sudo, so i wanted to set ubuntu on startup to do the following: ```
sudo nautilus /media/disk
```
is there a way to also put my password in that terminal command?

and yes I am new to Linux.

---

### Post by ibuclaw on 2008-06-05
Ubuntu can automount partitions for you, why this isn't doing it by default is the real question.

Can you post the output of these commands:
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

Regards
Iain

---

### Post by Het Irv on 2008-06-05
Have you tried this?
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If so where did you have problems?

---

### Post by tippx on 2008-06-05
> **tinivole said:**
> Ubuntu can automount partitions for you, why this isn't doing it by default is the real question.

Can you post the output of these commands:
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

Regards
Iain

for fdisk -l:
> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       23786   191004817+   7  HPFS/NTFS
/dev/sda3           23787       30394    53078760    5  Extended
/dev/sda5           23787       30118    50861758+  83  Linux
/dev/sda6           30119       30394     2216938+  82  Linux swap / Solaris

Disk /dev/sdb: 4110 MB, 4110230016 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f21e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         499     4008186    b  W95 FAT32

cat /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=de6516be-1e3c-4e0c-a4ac-21e4df92a4a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cb12fab6-48de-4be7-85a2-200a3d3b76a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



another thing i did not say, the windows partition does show up on the side in nautilus, but it says >  Cannot mount volume, Unable to mount the volume. , mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

---

### Post by Barriehie on 2008-06-05
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=de6516be-1e3c-4e0c-a4ac-21e4df92a4a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cb12fab6-48de-4be7-85a2-200a3d3b76a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```It looks like /dev/sda2 is your windows partition and you should be able to auto-mount it by adding this to your /etc/fstab file.  To edit the file you'll have to have root privelages.  You'll have to make a directory to be a mount point for the partition.  I use _*/home/barrie/windoze*_ on my machine.  So, from a terminal enter **gksudo gedit /etc/fstab **and enter your password when prompted and gedit will open your fstab file.
Add this to the end:
```

/dev/sda2 _*mountpoint directory you created*_ auto rw,auto,exec,user 0 0

```Note that the trailing 0 (zero) on the end of the line will NOT enable fsck to check the drive for errors.

Let us know if this helps!
Barrie

Oh yeah, you'll have to reboot after saving the new fstab file for the changes to show up.  This should make it visible in nautilus.  Not much to make a link on the desktop either!

---

### Post by tippx on 2008-06-06
> **Barriehie said:**
> ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=de6516be-1e3c-4e0c-a4ac-21e4df92a4a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cb12fab6-48de-4be7-85a2-200a3d3b76a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```It looks like /dev/sda2 is your windows partition and you should be able to auto-mount it by adding this to your /etc/fstab file.  To edit the file you'll have to have root privelages.  You'll have to make a directory to be a mount point for the partition.  I use _*/home/barrie/windoze*_ on my machine.  So, from a terminal enter **gksudo gedit /etc/fstab **and enter your password when prompted and gedit will open your fstab file.
Add this to the end:
```

/dev/sda2 _*mountpoint directory you created*_ auto rw,auto,exec,user 0 0

```Note that the trailing 0 (zero) on the end of the line will NOT enable fsck to check the drive for errors.

Let us know if this helps!
Barrie

Oh yeah, you'll have to reboot after saving the new fstab file for the changes to show up.  This should make it visible in nautilus.  Not much to make a link on the desktop either!
Thank you this fixed it.

---

### Post by Barriehie on 2008-06-06
Glad to help!  Don't forget to mark the thread solved.  That will be in the drop-down under thread tools that is in red at the top.

Barrie

---

