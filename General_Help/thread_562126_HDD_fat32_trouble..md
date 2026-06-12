---
title: "HDD fat32 trouble."
date: 2007-09-28
forum: General Help
---

### Post by Qaowuon on 2007-09-28
<SOLVED> w00t :D

I've searched the forums and found nothing, maybe because i didnt use the right phrases but anyway...

I have 2 hdd's. On my first HDD i have 4 partitions, all fat32 and all windows. On my second HDD Ubuntu.
Now to the point.
Sometimes when i boot Ubuntu it tells me HDA2 is a 10GB partition and sometimes it tells me its a 60GB (the one i want) partition.
The 10GB is a backup but somehow seems to be confused with the 60GB main partition.

Here is my Fstab file:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e9573b5d-f3c1-4011-95fc-79c23957e638 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=d0fbaa5e-78ea-4a78-b608-561bb0cbb16c /home           ext3    defaults        0       2
# /dev/hda1
UUID=9A56-1E94  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
**UUID=1406-DE64**  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
**UUID=1406-DE64**  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=5624DACA24DAABED /media/hda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=99737e55-935c-4d97-90ba-5a336f42f745 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



I hope anyone can help me with this, somewhat annoying, problem.

Regards.

---

### Post by mcduck on 2007-09-28
It's no surprise if you have problems with those partitions when they have the same UUID's in /etc/fstab :D

Run 'ls -la /dev/disk/by-uuid' or 'blkid' to get the right UUID's for those partitions, and then change the fstab to use those correct UUID's.

---

### Post by Qaowuon on 2007-09-28
before i stirr in the guts of my pc :)
how do i change the UUID of one of the partitions?

---

### Post by mcduck on 2007-09-28
> **Qaowuon said:**
> before i stirr in the guts of my pc :)
how do i change the UUID of one of the partitions?

you can't change the UUID of the partition. You should check what UUID the partition has, and then edit /etc/fstab so it has correct UUID.

In Gnome, press Alt-F2 and run 'gksudo gedit /etc/fstab' to edit the file. If you need to do it from command line use 'sudo nano /etc/fstab'.

---

### Post by Qaowuon on 2007-09-28
hmmm

i want to correct this problem but i am unable to actually find HDA3 with ls -la /dev/disk/by-uuid.
When i use that i get this:
> 
-----@-----:~$ ls -la /dev/disk/by-uuid
totaal 0
drwxr-xr-x 2 root root 160 2007-09-28 15:55 .
drwxr-xr-x 5 root root 100 2007-09-28 17:55 ..
lrwxrwxrwx 1 root root  10 2007-09-28 15:55 1406-DE64 -> ../../hda2
lrwxrwxrwx 1 root root  10 2007-09-28 17:55 5624DACA24DAABED -> ../../hda4
lrwxrwxrwx 1 root root  10 2007-09-28 17:55 99737e55-935c-4d97-90ba-5a336f42f745 -> ../../hdb3
lrwxrwxrwx 1 root root  10 2007-09-28 17:55 9A56-1E94 -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-09-28 17:55 d0fbaa5e-78ea-4a78-b608-561bb0cbb16c -> ../../hdb2
lrwxrwxrwx 1 root root  10 2007-09-28 17:55 e9573b5d-f3c1-4011-95fc-79c23957e638 -> ../../hdb1

and i cant find HDA3 (the troublesome partition)

and with blkid i get:
> 
/dev/hda1: SEC_TYPE="msdos" UUID="9A56-1E94" TYPE="vfat" 
/dev/hda2: UUID="1406-DE64" TYPE="vfat" 
/dev/hda3: UUID="1406-DE64" TYPE="vfat" 
/dev/hda4: TYPE="ntfs" 
/dev/hdb1: UUID="e9573b5d-f3c1-4011-95fc-79c23957e638" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb2: UUID="d0fbaa5e-78ea-4a78-b608-561bb0cbb16c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb3: UUID="99737e55-935c-4d97-90ba-5a336f42f745" TYPE="swap" 


where HDA2 and HDA3 have the same UUID again.
:confused:

---

### Post by mcduck on 2007-09-28
> **Qaowuon said:**
> hmmm

i want to correct this problem but i am unable to actually find HDA3 with ls -la /dev/disk/by-uuid.
When i use that i get this:

and i cant find HDA3 (the troublesome partition)

and with blkid i get:


where HDA2 and HDA3 have the same UUID again.
:confused:

Now that is strange!

You could try changing the fstab to mount those partitions based on their device names instead of UUID, it might help. But it should be pretty imossible for two different partitions to have the same UUID so there might be something wrong with your disks partition table..

Anyway, try changing the fstab like this and see what happens:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=e9573b5d-f3c1-4011-95fc-79c23957e638 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb2
UUID=d0fbaa5e-78ea-4a78-b608-561bb0cbb16c /home ext3 defaults 0 2
# /dev/hda1
UUID=9A56-1E94 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2
/dev/hda2 /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda3
/dev/hda3 /media/hda3 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda4
UUID=5624DACA24DAABED /media/hda4 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb3
UUID=99737e55-935c-4d97-90ba-5a336f42f745 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

---

### Post by Qaowuon on 2007-09-28
It seems to be working now, i have acces to all my partitions :D
thank you

---

