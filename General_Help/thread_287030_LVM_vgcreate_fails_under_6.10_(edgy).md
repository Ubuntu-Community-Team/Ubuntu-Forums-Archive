---
title: "LVM vgcreate fails under 6.10 (edgy)"
date: 2006-10-28
forum: General Help
---

### Post by EmmEff on 2006-10-28
First off, this is strange:

```

root@media:~# pvcreate /dev/hda3
  Failed to write physical volume "/dev/hda3"
root@media:~# pvcreate /dev/hda3
  Physical volume "/dev/hda3" successfully created
root@media:~# pvcreate /dev/hda3
  Failed to write physical volume "/dev/hda3"
root@media:~# pvcreate /dev/hda3
  Physical volume "/dev/hda3" successfully created
root@media:~# pvcreate /dev/hda3
  Failed to write physical volume "/dev/hda3"
root@media:~# pvcreate /dev/hda3
  Physical volume "/dev/hda3" successfully created

```

Is this normal?

After I do 'pvcreate', I attempt to create the volume group:

```

root@media:~# vgcreate storage /dev/hda3
  No physical volume label read from /dev/hda3
  /dev/hda3 not identified as an existing physical volume
  Unable to add physical volume '/dev/hda3' to volume group 'storage'.

```

Figuring it wasn't happy with the device name, I thought I'd try to use the UUID.  No such luck, I don't have one for this device:

```

root@media:~# ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2006-10-28 11:43 1d1d19ee-c389-424f-b5c7-4299929e9f36 -> ../../hda2
lrwxrwxrwx 1 root root 10 2006-10-28 11:43 5583c1d0-3dd2-4e9d-a8db-d3bd8f7e79b7 -> ../../hda1

```

More info...

```

root@media:~# sfdisk -l /dev/hda

Disk /dev/hda: 30515 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1          0+   1274    1275-  10241406   83  Linux
/dev/hda2       1275    1397     123     987997+  82  Linux swap / Solaris
/dev/hda3       1398   30514   29117  233882302+  8e  Linux LVM
/dev/hda4          0       -       0          0    0  Empty

```

I'm a bit disappointed that Edgy was a step backwards from my rock solid Dapper installation.

Can anybody help here?  Admittedly I've been using LVM for a while now, but everything I've done up until now has been successful so my LVM troubleshooting skills are non-existent.

---

### Post by EmmEff on 2006-10-29
I had to use device name "/dev/evms/hda3".

Is this documented somewhere?  I've never had to do this before, but I'm not familiar with EVMS and it's interaction with the system and LVM.

---

### Post by pielgrzym on 2006-11-03
Yes, this is normal - it occured in Dapper too :)

---

