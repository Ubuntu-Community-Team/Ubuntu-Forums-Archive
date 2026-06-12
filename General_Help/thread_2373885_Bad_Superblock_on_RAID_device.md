---
title: "Bad Superblock on RAID device"
date: 2017-10-10
forum: General Help
---

### Post by rsteinmetz70112 on 2017-10-10
I have a raid array which reverted during some unrelated configuration. I cannot get it to come back. It appears that mdadm recognizes the existing file system but somehow the superblocks are not right. 

This works and created the device.
```

# mdadm --create /dev/md2 --level=1 --raid-devices=2 /dev/sdc2 /dev/sdd2
mdadm: /dev/sdc2 appears to contain a reiserfs file system
       size = 460090304K
mdadm: /dev/sdc2 appears to be part of a raid array:
       level=raid1 devices=2 ctime=Mon Oct  9 15:28:12 2017
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: /dev/sdd2 appears to contain a reiserfs file system
       size = 460090304K
mdadm: /dev/sdd2 appears to be part of a raid array:
       level=raid1 devices=2 ctime=Mon Oct  9 15:28:12 2017
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md2 started.[/CODR]

However when I try to mount the device I get this.

[CODE]# mount /dev/md2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md2,
       missing codepage or helper program, or other error
```

---

### Post by rsteinmetz70112 on 2017-10-11
I finally solved it I have to rebuild the super block and check the filesystem but it's now loading.

---

