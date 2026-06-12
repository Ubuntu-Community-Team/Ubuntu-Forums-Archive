---
title: "Permission not granted :s"
date: 2007-02-26
forum: General Help
---

### Post by jhp-dk on 2007-02-26
Hey,

I have this little problem setting up my /etc/fstab so i can get read write and execute-permission to a paration on my internal-disk (hda5) and the same permissions to an external HDD ((sda1, not mentioned in fstab yet) which is normally turned on at boot and not plugged out. Both drives are fat32, so I can use them as "shared" folder between Windows (eventhough I dont use the crap anymore) and Ubuntu.

hda5 har /media/fatdisk as mountpoint and sda1 has none, yet...

```
 jhp@jhplin:~$ sudo nano /etc/fstab
#/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=147b573a-2a21-401d-a473-c5ba9c56b4de /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=04f95579-532d-4879-b73b-44c6a3a32e73 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb2       /media/iPod     vfat    user,noauto,umask=000   0       0
/dev/hda5       /media/fatdisk  vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0

```

```
jhp@jhplin:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1278    10265503+   c  W95 FAT32 (LBA)
/dev/hda2            1279        5196    31471335    f  W95 Ext'd (LBA)
/dev/hda3            5197        7299    16892347+  83  Linux
/dev/hda5            1279        5102    30716248+   b  W95 FAT32
/dev/hda6            5103        5196      755023+  82  Linux swap / Solaris

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    c  W95 FAT32 (LBA)

```

THANKS

---

### Post by netkid91 on 2007-02-26
FAT32 doesn't support permissions, end of story.

---

### Post by bodhi.zazen on 2007-02-26
Permissions are handled at the time of mount.

Your umask=000 should give you full permissions.

If you want finer control use dmask and fmask

See man mount for details : [http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

Your fstab entry looks OK to me, what problem are you having ?

---

### Post by jhp-dk on 2007-02-27
The problem is that I'm using hda5 as a download folder for almost everything and when i down archives they wont open and extract, but I'm downloading the same files to my desktop there no problem at all... 

sda1 is used for personal documents, music etc....

Thanks

---

