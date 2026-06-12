---
title: "monting HDD on boot"
date: 2008-07-01
forum: General Help
---

### Post by hirohitosan on 2008-07-01
Greetings
I added an new HDD to my box and I formated but now I don't know how to mount it when the system starts.
Now my fstab looks like
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=91a74893-8324-4f0c-89c0-d6d0e1a9b492 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=694fff24-7e13-4c75-8537-779396c164c2 /home           ext3    relatime        0       2
# /dev/sda1
UUID=bc428c4a-db0f-41d4-9a6d-3725423f4bdb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

my new hdd is in /dev/sdb1

and I don't understand what is 
UUID=91a74893-8324-4f0c-89c0-d6d0e1a9b492 ?

any help?
thanks

---

### Post by soccerboy on 2008-07-01
that is like a unique id for the start address of the partition.  What is your fdisk -l output.
and ls -l /dev/disk/by-uuid output

---

### Post by kpkeerthi on 2008-07-01
> **hirohitosan said:**
> my new hdd is in /dev/sdb1

and I don't understand what is 
UUID=91a74893-8324-4f0c-89c0-d6d0e1a9b492 ?

any help?
thanks

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by Vivaldi Gloria on 2008-07-01
```
ls /dev/disk/* -lah

sudo blkid
```

gives info about your disks. every partition has a unique uuid. find the uuid of your new disk and add it to fstab as follows:

```
UUID=your_disk's_uid  /mnt/mountpoint      ext3    relatime        0       2
```

To do this first create the mountpoint folder.

See also

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by hirohitosan on 2008-07-01
```
fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           60316       60801     3903795   82  Linux swap / Solaris
/dev/sda2   *           1       12158    97659103+  83  Linux
/dev/sda3           12159       60315   386821102+   5  Extended
/dev/sda5           12159       60315   386821071   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000217fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

and 

```
 ls -l /dev/disk/by-uuid output
ls: cannot access output: No such file or directory
/dev/disk/by-uuid:
total 0
lrwxrwxrwx 1 root root 10 2008-07-01 09:18 200ad04b-7351-42b1-9821-1a24dc78b88d -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-07-01 09:14 694fff24-7e13-4c75-8537-779396c164c2 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-07-01 09:14 91a74893-8324-4f0c-89c0-d6d0e1a9b492 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-07-01 09:14 bc428c4a-db0f-41d4-9a6d-3725423f4bdb -> ../../sda1

```

---

### Post by Vivaldi Gloria on 2008-07-01
First make the folder where you are going to mount the hard disk, for example /mnt/mountpoint. Then add this to fstab:


```
UUID=200ad04b-7351-42b1-9821-1a24dc78b88d  /mnt/mountpoint      ext3    relatime        0       2
```

---

### Post by soccerboy on 2008-07-01
> **Vivaldi Gloria said:**
> ```
ls /dev/disk/* -lah

sudo blkid
```

gives info about your disks. every partition has a unique uuid. find the uuid of your new disk and add it to fstab as follows:

```
UUID=your_disk's_uid  /mnt/mountpoint      ext3    relatime        0       2
```

To do this first create the mountpoint folder.

See also

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


So, add this line to your fstab
UUID=200ad04b-7351-42b1-9821-1a24dc78b88d /mnt/mountpoint            ext3    relatime        0       2[/code]

should allow automount then

Someone please double check.  I am assuming sdb1 is the new drive you want.

---

