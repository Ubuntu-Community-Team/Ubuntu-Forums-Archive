---
title: "Unable to change file/directory permissions as root"
date: 2008-01-06
forum: General Help
---

### Post by KunoNoOni on 2008-01-06
I have a hard drive with 3 partitions on it that were originally in the system when it had windows xp on it. I have since installed another hardrive that I've put ubuntu on and when I boot up the 3 old windows partitions are mounted automatically. All the files and directories on these partitions are owned by root and are in the plugdev group. The permissions on all the directories and files are set to 770. I'm trying to set them all to 777 but when I try ```
sudo chmod 777 *
``` I get an error that the Operation is not permitted. I'm at a loss as to why this is happening. I checked /etc/group and my user is part of plugdev. If there is any other information I need to give just let me know.

---

### Post by PurposeOfReason on 2008-01-06
You can't just *. You'd have to do it like
chmod 777 /vista/* (or just /vista)

---

### Post by KunoNoOni on 2008-01-06
Hmm, I just tried ```
sudo chmod 777 ~/DriveF/hdb7/*
``` I got no error but the permissions have not changed. This is really weird... I've never encountered anything like this before...

---

### Post by PurposeOfReason on 2008-01-06
> **KunoNoOni said:**
> Hmm, I just tried ```
sudo chmod 777 ~/DriveF/hdb7/*
``` I got no error but the permissions have not changed. This is really weird... I've never encountered anything like this before...
Try a ```
chown -R YOURUSERNAME ~/DriveF/hdb7/
```
No * either. Is  ~/DriveF/hdb7/ it's mountpoint or did you mount it to something like /storage? Use whatever you mount it to.

---

### Post by KunoNoOni on 2008-01-06
I tried it and I still get *Operation not permitted*

---

### Post by PurposeOfReason on 2008-01-06
Are you root?

sudo chown -R YOURUSERNAME ~/DriveF/hdb7/

---

### Post by KunoNoOni on 2008-01-06
I know you had to ask this question, yes I have tried with and without sudo. I get the same results :) thats whats so weird, Root is suppose to have full access over the entire system. Yet I am unable to change the permissions of these directories or files...

---

### Post by PurposeOfReason on 2008-01-06
And  I'm guessing you did use your username, not what I typed? Please post your /etc/fstab and tell me which one you're changing.

---

### Post by zero-9376 on 2008-01-06
you may want to try unmounting the partition then changing ownership/permisions of the mount point itself then remount the paritions

sudo chown user:user ~/DriveF/hdb7 

although as it is in you home directory you may already own the mount directory

maybe post you /etc/fstab

---

### Post by bodhi.zazen on 2008-01-06
LOL

Permissions depend of the file system. I assume you are talking about a FAT of NTFS partition. In that event permissions / ownership is set at the time of mount.

mount /dev/sdxy /mount/point -o uid=1000,gid=100,umaks=007

Or a fstab entry :

/dev/sdxy /mount/point ntfs-3g auto,usres,uid=100,gid=100,umask=007 0 0

See these links : 

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by KunoNoOni on 2008-01-06
Here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=95f315fd-1a59-4fdc-8ca5-9628ed77ddb2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=7EB4-FC7A  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=BE7D-D147  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
[B]# /dev/hdb7
UUID=FE46-A618  /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1[/B]
# /dev/hda5
UUID=9dcedfd9-0363-4eb6-b431-51340590c6bc none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hdc1
/dev/hdc1	 /var/www/htdocs/media 	ext3 	defaults 0 	2
# /dev/hdc2
/dev/hdc2	/var/www/htdocs/media2	ext3	defaults 0	2
```

The one in bold is the one I'm trying to change

---

### Post by PurposeOfReason on 2008-01-06
Two things that were critical to say.
1. It's a fat32 partition
2. The mountpoint is /media/hdb7

Read the post before yours. It says how to mount a fat32 partition to read a write. Do those changes and reboot.

---

### Post by KunoNoOni on 2008-01-07
Hmm, ok will give it a try and let you all know what the outcome is. Not tonight though... its getting late and I don't want to edit the fstab tired... ;)

---

### Post by bodhi.zazen on 2008-01-07
FYI : you do not need to re-boot. Just unmount and re-mount the partition after editing fstab.

---

### Post by KunoNoOni on 2008-01-08
LOL

Wow thanks for all your help with this problem. It worked!!

---

