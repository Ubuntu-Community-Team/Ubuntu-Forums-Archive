---
title: "[SOLVED] Flash drive won't mount"
date: 2008-02-23
forum: General Help
---

### Post by L815 on 2008-02-23
I plug in my flash drive, it flashes a couple of times, and nothing happens.

This is the output of fdisk -l

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x978a4836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193       28496   227347876    7  HPFS/NTFS
/dev/sda3           28497       30198    13671315   83  Linux
/dev/sda4           30199       30401     1630597+  82  Linux swap / Solaris

Disk /dev/sdb: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00286cf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         251     2015200+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 39)


```

When I try mounting it in terminal, I get this:
```

l815@l815-laptop:~$ mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

```

---

### Post by taurus on 2008-02-23
What happens when you run these from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by L815 on 2008-02-23
Wow it worked. Thanks!!!:)

---

### Post by taurus on 2008-02-23
_Remember_ to unmount it first before you unplug it.

```
sudo umount /media/sdb1
df -h
```

---

### Post by L815 on 2008-02-24
How do I get it to mount automatically when I plug it in?

---

