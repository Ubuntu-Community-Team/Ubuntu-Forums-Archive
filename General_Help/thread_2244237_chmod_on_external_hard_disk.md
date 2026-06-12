---
title: "chmod on external hard disk"
date: 2014-09-14
forum: General Help
---

### Post by ELMIT on 2014-09-14
I got a nice 3TB hard disk.

cd /media/ronald/Seagate Expansion Drive/

touch 111

ls -l 111
-rw------- 1 ronald ronald 0 Sep 15 08:51 111

chmod 666 111
ls -l 111
-rw------- 1 ronald ronald 0 Sep 15 08:51 111

sudo chmod 666 111
ls -l 111
-rw------- 1 ronald ronald 0 Sep 15 08:51 111

cat /etc/mtab
...
/dev/sdc1 /media/ronald/Seagate\040Expansion\040Drive fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0


What do I need to do to get full control on that drive???

---

### Post by JKyleOKC on 2014-09-14
Try this:
```

sudo mount /dev/sdc1 /media/ronald/Seagate\040Expansion\040Drive -o rw,user,noauto,umask=0,uid=1000,remount

```Setting the "umask" and "uid" options should convert the device's mount to permissions of rwx for all users, and UID 1000 as the owner.

I've not tested this since I don't have any similar drives, but have often used the "remount" option to change permissions for thumb drives when the system insisted on assigning ownership to root and read-only permissions for other users...

---

### Post by Habitual on 2014-09-14
Is it shared with a Windows OS on this computer?
or...
I'm wondering why fuse is being used? (Yes, I understand it may be an ntfs partition and ntfs-3g uses it.)

---

### Post by ELMIT on 2014-09-14
it is only used for Linux, just plugged in the device and that came out ;-)

sudo mount /dev/sdc1 /media/ronald/Seagate\040Expansion\040Drive -o rw,user,noauto,umask=0,uid=1000,remount
mount: you must specify the filesystem type

sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

...

Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x90b70a23

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   732566644  2930258388    7  HPFS/NTFS/exFAT

---

### Post by JKyleOKC on 2014-09-14
Try again, adding "-t fuseblk" just before the "-o" in the command I suggested earlier. I took the type from the error message in your original post; unfortunately since I can't test here I don't know whether it will work or not but it's worth a try.

The "remount" option lets you make some changes, but doesn't work with all of the possible parameters. I usually use it with nothing but "rw,remount" after the "-o" argument. Be sure that the drive is already listed in mtab before trying the remount command.

---

### Post by ELMIT on 2014-09-14
sudo mount /dev/sdc1 /media/ronald/Seagate\ Expansion\ Drive/ -t fuseblk -o rw,user,noauto,umask=0,uid=1000,remount

ls -l /media/ronald/
drwx------ 1 ronald ronald 2088 Sep 14 14:44 Seagate Expansion Drive

chmod 777 /media/ronald/Seagate\ Expansion\ Drive/
ls -l /media/ronald/
drwx------ 1 ronald ronald 2088 Sep 14 14:44 Seagate Expansion Drive


test on a file on that drive:
chmod 777 111
ls -l 111
-rw------- 1 ronald ronald      0 Sep 15 08:51 111

mtab shows:
/dev/sdc1 /media/ronald/Seagate\040Expansion\040Drive fuseblk rw,noexec,nosuid,nodev,umask=0,uid=1000 0 0

---

### Post by JKyleOKC on 2014-09-14
It's possible that there's something in the "fuseblk" filesystem type that's preventing chmod from working in that system, in the name of increased security.

The "umask=0" in the remount command is intended to allow all data on the stick to have 777 permissions. Obviously it's not doing so. Hopefully someone more knowledgeable than myself when it comes to the fuse capabilities will jump in and take a look...

---

