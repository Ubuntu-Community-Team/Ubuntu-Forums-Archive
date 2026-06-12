---
title: "[SOLVED] Little fstab help"
date: 2007-11-04
forum: General Help
---

### Post by CrustyDOD on 2007-11-04
Right, its been a while since i did this and now in Gutsy things are changed.

basically right now i have all stuff on 1 partition and now i want to move /home to seperate partition. This is where i'm stuck. I have extra partition ext3 ready and formated but cannot get it to mount cause of that weird id's...

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=79439698-ed09-48fb-a676-bfcebd2ca442 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=FA80696780692AF9 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=E41C5C651C5C3530 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=C6F40CEBF40CE013 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
/dev/sda6 /home     ext3    defaults,auto 0     1
# /dev/sda9
UUID=FA041FA2041F6145 /media/sda9     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=07d89e23-ddc6-4ab2-98c9-ce418265328a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

# /dev/sda6
/dev/sda6 /home     ext3    defaults,auto 0     1

this used to be NTFS partition and everything worked but since i changed it in windows to ext3 i have to change fstab also but have no idea how..

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb67bb67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       60800   467893125    f  W95 Ext'd (LBA)
/dev/sda5            2551       15298   102398278+   7  HPFS/NTFS
/dev/sda6           15299       30496   122077903+  83  Linux
/dev/sda7   *       30497       40308    78814858+  83  Linux
/dev/sda8           40309       40794     3903763+  82  Linux swap / Solaris
/dev/sda9           40795       60800   160698163+   7  HPFS/NTFS

```

**/dev/disk/by-uuid** contains:
07d89e23-ddc6-4ab2-98c9-ce418265328a
79439698-ed09-48fb-a676-bfcebd2ca442
C6F40CEBF40CE013
E41C5C651C5C3530
FA041FA2041F6145
FA80696780692AF9

If i do sudo mount /home i won't be able to run anything as /home doesn't exist. Help please!

---

### Post by sisco311 on 2007-11-04
to get the uuid of /dev/sda6 type:
```
 sudo vol_id -u /dev/sda6
```then add this line to fstab:
> # /dev/sda6
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx    /home ext3    defaults    0    2replace xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx with the uuid

move(or copy) your home folder to your new home partition:
```
sudo mount /dev/sda6 /mnt
mv /home/username /mnt
```reboot

---

