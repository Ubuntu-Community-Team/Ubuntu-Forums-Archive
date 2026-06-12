---
title: "Logical Volume won't mount"
date: 2013-03-05
forum: General Help
---

### Post by kermtfrg on 2013-03-05
I ran into some major problems when I tried adding a new hard drive to my lvm.  I'm not sure what happened but I lost my logical volume.  The physical volumes and volume group are still there.  Tried creating the logical volume again but realized if I add a file system to it it says that it will erase the data on the physical volumes.  I've got 4TB worth of data that I don't want to lose.  Do I have any hope of getting my data back?  Is there anyway I can create a new logical volume that uses the existing physical volumes without erasing the data on the physical?

```
  --- Logical volume ---  LV Name                /dev/mediaserver/homeserver
  VG Name                mediaserver
  LV UUID                ax3phG-oLdJ-Dzz6-97Ql-fNX4-5ztk-CKf9Fs
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                8.99 TiB
  Current LE             2356143
  Segments               6
  Allocation             inherit
  Read ahead sectors     auto

```

```

jon@mediaserver:~$ sudo vgscan  Reading all physical volumes.  This may take a while...
  Found volume group "backup" using metadata type lvm2
  Found volume group "mediaserver" using metadata type lvm2

```

```
jon@mediaserver:~$ sudo lvscan  ACTIVE            '/dev/backup/lvbackup' [465.00 GiB] inherit
  ACTIVE            '/dev/mediaserver/root' [87.16 GiB] inherit
  ACTIVE            '/dev/mediaserver/swap_1' [5.96 GiB] inherit
  inactive          '/dev/mediaserver/homeserver' [8.99 TiB] inherit

```

```
jon@mediaserver:~$ sudo vgchange -ay mediaserver  device-mapper: create ioctl failed: Device or resource busy
  2 logical volume(s) in volume group "mediaserver" now active

```

---

