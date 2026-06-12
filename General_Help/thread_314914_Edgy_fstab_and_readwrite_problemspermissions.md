---
title: "Edgy fstab and read/write problems/permissions"
date: 2006-12-08
forum: General Help
---

### Post by MJSOnline on 2006-12-08
Hi all.  I have just installed Edgy on to my pc.  It has picked up my Win XP Pro partion and my 2nd hard drive FAT32 partion.

The problem is I dont want the poartions showing as hda1, hda2, hd1b etc.

Ho do I fix this so I can read/write onto them both?

If I add a 2nd or 3rd partion on the 2nd harddrive, for example and shared FAT32 space for my partner to save her work files to, just incase the work server falls over, again?

I include a copy of my cat /etc/fstab output..
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f49f4026-3626-4e7b-8a7d-e447daf397b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=34B43B8BB43B4F1C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=F4DF-7B50  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=6e9afc4d-c0a5-4075-91b9-1c11600945dd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

And fdisk -l

```
Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         656     5269288+   7  HPFS/NTFS
/dev/hda2            1049        1236     1510110   82  Linux swap / Solaris
/dev/hda3             657        1048     3148740   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2491    20008926    c  W95 FAT32 (LBA)
```


Thanks. Matthew

---

### Post by bodhi.zazen on 2006-12-08
> **MJSOnline said:**
> Hi all.  I have just installed Edgy on to my pc.  It has picked up my Win XP Pro partion and my 2nd hard drive FAT32 partion.

The problem is I dont want the poartions showing as hda1, hda2, hd1b etc.

What do you want them to show up as? 

Unmount the partitions, make a new mount point, delete the old mount point, and update fstab.

For example, with hda1 changing the name to data:```
sudo umount /media/hda1 && sudo rm /media/hda1 && sudo mkdir /media/data
```

Now change your entry in fstab to:> /dev/hda1 /media/hda1     ntfs defaults,nls=utf8,umask=007,gid=46 0 0 

> **MJSOnline said:**
> Ho do I fix this so I can read/write onto them both?

for ntfs you need to install [ntfs-3g](http://ubuntuforums.org/showthread.php?&t=217009)

for you FAT, just update fstab, unmount, and re-mount:

fstab:> /dev/hdb1 /media/vfat  vfat  users,utf8,umask=000  0  0

then, as before,```
sudo umount /media/hdb1 && sudo rm /media/hdb1 && sudo mkdir /media/vfat
mount /media/vfat
```

Use what name you will...

> **MJSOnline said:**
> If I add a 2nd or 3rd partion on the 2nd harddrive, for example and shared FAT32 space for my partner to save her work files to, just incase the work server falls over, again?

Not sure what you are asking. Just add an entry to fstab for each partition. You can manage wonership and privilages via gid=xyz or uid=xyz and umask=007 for example.

I do not foresee any degradation in performance....

See [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131) for further information....

> **MJSOnline said:**
>  I include a copy of my cat /etc/fstab output..

Hey, thanks for that..

You know to edit fstab:```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```

---

### Post by MJSOnline on 2006-12-08
Whoops!! Thanks.  I will try in out next.  Do the drives/partions show up correctly after a reboot i.e. auto mounting? M

---

### Post by bodhi.zazen on 2006-12-08
:lol: Look up.....

Hey, and don't forget we are all volunteers here

---

### Post by MJSOnline on 2006-12-08
> **bodhi.zazen said:**
> :lol: Look up.....

Hey, and don't forget we are all volunteers here

Thanks.  Thats true.  What does the  ```
/dev/hda1
UUID=34B43B8BB43B4F1C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
``` mean?  Can I delete the UUID part of it?

---

### Post by bodhi.zazen on 2006-12-08
> **MJSOnline said:**
> Thanks.  Thats true.  What does the  ```
/dev/hda1
UUID=34B43B8BB43B4F1C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
``` mean?  Can I delete the UUID part of it?

See the link for how to fstab.

In a nutshell you can refer to a partition to mount in several way.
[list=number][*]device /dev/hdxy
[*]label LABEL=xyz
[*]and [Universally Unique Identifier](http://en.wikipedia.org/wiki/UUID) UUID = Long number[/list]

There are additional ways, but that covers the most common....

And yes, it is "or" so the first entry on a line in fstab should be /dev/hdxyz, UUID=xyz, or LABEL=xyz:> 
/dev/hdxyz <mount_point> <file_system> <options> 0 0
UUID=xyz <mount_point> <file_system> <options> 0 0
LABEL=xyz<mount_point> <file_system> <options> 0 0

no need to list a partition more then once.....

To list your partitions, first connect the devices (including usb devices)

ls /dev/disk/by-uuid
ls /dev/disk/by-label

---

