---
title: "Remounting Windows partition"
date: 2007-01-05
forum: General Help
---

### Post by Veracon on 2007-01-05
Hi,

A while back I unmounted my Windows partition for a reason I don't quite recall. Now I'd like to remount it again, but I can't seem to find a way. In Dapper, I'm confident there was a GUI tool for mounting partitions under System > Administration, yet I can't find that here in Edgy. I obviously can't mount it with pmount since it's not removable.

Any help is appreciated. Thanks!

---

### Post by taurus on 2007-01-05
You can mount it by adding an entry in /etc/fstab.  I just need to know what partition your Windows is on before I can show you how to add it.  So, paste the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Veracon on 2007-01-05
Here's the entry for the Windows partition:
/dev/hda1   *           1        1216     9767488+   c  W95 FAT32 (LBA)

Appreciate the help!

---

### Post by taurus on 2007-01-05
Okay, you need to edit /etc/fstab to add an entry for that harddrive/partition.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the bottom of the file and add the following line to it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create a mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```
And from now on, everytime you boot Ubuntu, your Windows will be mounted to /media/hda1...

---

### Post by Veracon on 2007-01-06
Thanks heaps, it works great!

---

### Post by taurus on 2007-01-06
You're welcome.

---

### Post by Jaygo333 on 2007-01-10
Hey, Im also trying to mount my windows Drive but im not succesful
the info on my sudo fdisk -l is
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2664    21398548+   7  HPFS/NTFS
/dev/sda2            2665        9039    51207187+   f  W95 Ext'd (LBA)
/dev/sda5            2665        9039    51207156    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

I looked at your solution for him but it seems he has a FAT file system.
Will it work on me, I have NTFS, is please help, I wanna migrate from Windows completely.

---

### Post by taurus on 2007-01-10
> **Jaygo333 said:**
> Hey, Im also trying to mount my windows Drive but im not succesful
the info on my sudo fdisk -l is
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2664    21398548+   7  HPFS/NTFS
/dev/sda2            2665        9039    51207187+   f  W95 Ext'd (LBA)
/dev/sda5            2665        9039    51207156    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

I looked at your solution for him but it seems he has a FAT file system.
Will it work on me, I have NTFS, is please help, I wanna migrate from Windows completely.

Okay, so I assume you want to mount both /dev/sda1 & /dev/sda5 then.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Then, add the following two lines to the end of it.

```

/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   ntfs   nls=utf8,umask=0222   0   0

```
Save it and create the two new mount points.

```
sudo mkdir /media/sda1 /media/sda5
sudo mount -a
df -h
```

---

