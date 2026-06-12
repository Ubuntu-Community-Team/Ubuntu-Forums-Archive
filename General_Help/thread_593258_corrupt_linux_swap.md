---
title: "corrupt linux swap"
date: 2007-10-27
forum: General Help
---

### Post by azray on 2007-10-27
My device /dev/sda3 on MD1 part of my raid system is unknown (corrupt). Is there a way to fix this problem? I thought of deleting the bad partition but am unsure if it would be recreated say if rebooted???

Any suggestions are welcome as it is affecting performance.

P4, 2-80gb raid, 1 gb mem

---

### Post by nixclusive on 2007-10-27
if you know the exact device name (/dev/sda3?).. you can re-format it for swap usage:
```
sudo swapoff <device>
sudo mkswap -v1 <device>
sudo swapon <device>
```
Hope this helps..

---

### Post by azray on 2007-10-27
result:

desktop:~$ sudo swapoff /dev/sda3
swapoff: /dev/sda3: Invalid argument

Also get the following when running gparted;
Unable to open /dev/md2 - unrecognised disk label.

---

### Post by taurus on 2007-10-27
What about

```
sudo fdisk -l
```

---

### Post by azray on 2007-10-27
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051b2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6687    53713296   fd  Linux raid autodetect
/dev/sda2            6688        9605    23438835   fd  Linux raid autodetect
/dev/sda3            9606        9702      779152+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6687    53713296   fd  Linux raid autodetect
/dev/sdb2            6688        9605    23438835   fd  Linux raid autodetect
/dev/sdb3            9606        9702      779152+  fd  Linux raid autodetect

Disk /dev/md0: 55.0 GB, 55002333184 bytes
2 heads, 4 sectors/track, 13428304 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/md1: 24.0 GB, 24001249280 bytes
2 heads, 4 sectors/track, 5859680 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

---

### Post by azray on 2007-10-29
I have no swap file on either drive and swapon will not work....Heeelllppp

---

