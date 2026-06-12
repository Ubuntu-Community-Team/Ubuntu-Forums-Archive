---
title: "No NTFS Drives"
date: 2006-12-16
forum: General Help
---

### Post by hadiriazi on 2006-12-16
Hey Guys;
This is the problem I'm having, After starting my box a message appeared on the black screen saying: sda9 has been mounted more than 30 times, checking and scanning the disk.

After the check completed it nicely booted to my 'buntu, but I noticed that don't have my NTFS drives any more!!

What should I do? I've been using 3g ntfs so I could have R/W abilities.

---

### Post by taurus on 2006-12-16
What does your /etc/fstab look like then and harddrive too?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by hadiriazi on 2006-12-16
```
**sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3939    31639986    7  HPFS/NTFS
/dev/sda2            3940       19456   124640302+   f  W95 Ext'd (LBA)
/dev/sda5            3940        9166    41985846    7  HPFS/NTFS
/dev/sda6            9167       14393    41985846    7  HPFS/NTFS
/dev/sda7           14394       18947    36579973+   7  HPFS/NTFS
/dev/sda8           18948       18960      104391   83  Linux
/dev/sda9           18961       19456     3984088+  83  Linux
```


```
**cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=157fec44-7687-4a6f-ad0b-377f3a765a3f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=be8be360-6f4b-42b3-bf63-0d5743dc992e /boot           ext3    defaults        0       2
# /dev/sda1
UUID=2EB843B9B8437E79 /media/sda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=D8BC8DB7BC8D9124 /media/sda5     ntfs-3g    defaults,nls=en_US.iso885915,umask=007,gid=46 0       1
# /dev/sda6
UUID=6C54979154975D20 /media/sda6     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=C0A8A033A8A02A3C /media/sda7     ntfs    defaults,locale=en_US.utf8,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2006-12-17
Try to change the last value for ntfs from 1 back to 0!!!

```

UUID=2EB843B9B8437E79 /media/sda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=D8BC8DB7BC8D9124 /media/sda5     ntfs-3g   defaults,nls=en_US.iso885915,umask=007,gid=46 0       0
UUID=6C54979154975D20 /media/sda6     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=C0A8A033A8A02A3C /media/sda7     ntfs    defaults,locale=en_US.utf8,umask=007,gid=46 0   0

```
p.s.  Interesting that you want to read/write to the first three but only read for the last ntfs partition, /dev/sda7...

---

### Post by hadiriazi on 2006-12-17
> **taurus said:**
> Try to change the last value for ntfs from 1 back to 0!!!

```

UUID=2EB843B9B8437E79 /media/sda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=D8BC8DB7BC8D9124 /media/sda5     ntfs-3g   defaults,nls=en_US.iso885915,umask=007,gid=46 0       0
UUID=6C54979154975D20 /media/sda6     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=C0A8A033A8A02A3C /media/sda7     ntfs    defaults,locale=en_US.utf8,umask=007,gid=46 0   0

```
p.s.  Interesting that you want to read/write to the first three but only read for the last ntfs partition, /dev/sda7...

I tried what you told me but still the same!! :(
*[COLOR="DimGray"]P.S change that last line "sda7" ntfs to ntfs-3g thanks[/COLOR]*

---

### Post by taurus on 2006-12-17
After making the changes to your /etc/fstab, did you mount them again with

```
sudo mount -a
df -h
```

---

### Post by hadiriazi on 2006-12-17
ok Problem Solved.

**Case:** No NTFS drives showing up
**Cause:** Improper shutdown (Windows)
**Solution:** Booted to windows and restarted PC

*P.S **Thanks taurus**, BTW whats the difference between the 0 and 1 at the end of the fstab lines?*

---

### Post by taurus on 2006-12-17
0 tells the system not to scan the disk while 1 scans the disk after how many mounts.  Normally, you only want to scan ext2/ext3 but not vfat or ntfs.  Therefore, you want to use "0  0" for vfat and ntfs/ntfs-3g.

---

### Post by hadiriazi on 2006-12-17
Thanks, changed them back to 0's, but now I dont see my non english folders anymore??

---

### Post by taurus on 2006-12-17
For which partitions?

---

### Post by hadiriazi on 2006-12-17
> **taurus said:**
> For which partitions?

For all of my NTFS !

---

### Post by hadiriazi on 2006-12-17
bump :-k

---

