---
title: "Can't mount FAT32 external hdd: can't read superblock"
date: 2008-04-11
forum: General Help
---

### Post by Mchl923 on 2008-04-11
OK, so I have an external hdd with ALL of my (and my family members') important data stored on it (I recently reinstalled windows and moved important data onto the external).  When i try to mount now I get the error "cannot mount volume" details are "mount: /dev/sdc1: can't read superblock"

any help?

---

### Post by dcstar on 2008-04-11
> **Mchl923 said:**
> OK, so I have an external hdd with ALL of my (and my family members') important data stored on it (I recently reinstalled windows and moved important data onto the external).  When i try to mount now I get the error "cannot mount volume" details are "mount: /dev/sdc1: can't read superblock"

any help?

**You** should not have to mount anything, external drives are auto-mounted on plug-in unless there is a problem with the filesystem.

Exactly what are you doing?

---

### Post by ruy_lopez on 2008-04-11
> **Mchl923 said:**
> When i try to mount now I get the error "cannot mount volume" details are "mount: /dev/sdc1: can't read superblock"

FAT partitions don't have superblocks. "mount" is complaining because it thinks the drive is an ext3 partition (which is the default). To mount a FAT partition you need to provide the type:

```

mount -t vfat /dev/sdc1 /path/to/mountpoint

```

---

