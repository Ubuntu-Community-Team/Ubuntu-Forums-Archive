---
title: "Mount Hard Drive"
date: 2006-10-13
forum: General Help
---

### Post by dontgetshocked on 2006-10-13
I cant mount my xp hard drive, any ideas why?
It doesn't see it in Nautilus and cant mount thru Places/Computer

---

### Post by divague on 2006-10-13
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by Kateikyoushi on 2006-10-13
You need to mount the partitions to be able to use them, this command will list them.

```
sudo fdisk -l
```

Then follow these steps [LINK.]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

If you get stuck, copy here the output of the fdisk command and also your /etc/fstab with this line.

```
cat /etc/fstab
```

---

### Post by dontgetshocked on 2006-10-13
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdf1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdf5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Hope this makes sense to you, not me for sure.
I do have the hd shared, at least some folders for sure.
What should I do next?
:neutral:

---

### Post by xmastree on 2006-10-13
As Kateikyoushi said, please run this command:
**sudo fdisk -l**
and post the results here.

It will tell us the location of the hard disk in question, then we can help you to mount it.

---

### Post by dontgetshocked on 2006-10-16
Disk /dev/hdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1        9351    75111876   83  Linux
/dev/hdf2            9352        9729     3036285    5  Extended
/dev/hdf5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1        9728    78140128+   7  HPFS/NTFS

---

### Post by Kateikyoushi on 2006-10-16
Okay we make a mount point for that drive, then edit the fstab so it will be mounted automatically.
Copy the commands to terminal

```
sudo mkdir /media/hdg1
```

Create a backup of fstab
```
sudo cp /etc/fstab /etc/fstab_old
```

Now we modify the fstab

```
sudo nano /etc/fstab
```

Add this line to the end.
```
/dev/hdg1 /media/hdg1 ntfs  nls=utf8,umask=0222 0    0
```

Save and exit wih CTRL+X and Yes to write changes to disc.

Now remount fstab

```
sudo mount -a
```

Then go to /media/hdg1 and check whather it is there.

---

### Post by CatKiller on 2006-10-16
```
sudo cp /etc/fstab **/etc/**fstab_old
``` :)

---

### Post by Kateikyoushi on 2006-10-16
Thanks I corrected, gets a bit cold, makes typing bit difficult.

---

