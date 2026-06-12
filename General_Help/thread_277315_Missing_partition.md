---
title: "Missing partition"
date: 2006-10-14
forum: General Help
---

### Post by JamesB on 2006-10-14
I've just installed elive on to a partition (hda6). Then re-set grub using the ubuntu live cd, now the partiton elive is on doesn't show in ubuntu (hda5) or in edgy (hda7). file system not changed.

I checked fstab and looks ok.

Any ideas please.

---

### Post by Kateikyoushi on 2006-10-14
Could you show us your fstab and the partition layout ?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by JamesB on 2006-10-14
> **Kateikyoushi said:**
> Could you show us your fstab and the partition layout ?

```
sudo fdisk -l
cat /etc/fstab
```


fdisk:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/hda2             244        2159    15390270    c  W95 FAT32 (LBA)
/dev/hda3            2160        2290     1052257+  82  Linux swap / Solaris
/dev/hda4            2291        9729    59753767+   f  W95 Ext'd (LBA)
/dev/hda5            2291        4248    15727603+  83  Linux
/dev/hda6   *        4249        6206    15727603+  83  Linux
/dev/hda7            6207        8164    15727603+  83  Linux
/dev/hda8            8165        9729    12570831    c  W95 FAT32 (LBA)


cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs notail          0       0
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hda6       /media/hda6     reiserfs defaults        0       0
/dev/hda7       /media/hda7     reiserfs defaults        0       0
/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       0/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Hope this helps, I've noticed an asterisk for boot to hda6, could this be the problem? if so, how do I change it?

James

---

### Post by Kateikyoushi on 2006-10-14
The asterisk show that the partition is bootable, that should not be the cause.

What happens when you try to mount it ?

```
sudo mount /media/hda6
```

---

### Post by JamesB on 2006-10-14
> **Kateikyoushi said:**
> The asterisk show that the partition is bootable, that should not be the cause.

What happens when you try to mount it ?

```
sudo mount /media/hda6
```

Just realised i had changed the filesystem to ext3, all seems ok now i've changed fstab. sorry, but thanx for your help. be interesting if it will be seen on reboot and in edgy??

---

### Post by Kateikyoushi on 2006-10-14
Good, do not forget to modify fstab on both of your OSes.

---

