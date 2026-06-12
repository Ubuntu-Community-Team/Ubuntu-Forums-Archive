---
title: "Need To Mount Hidden Partition Help"
date: 2008-06-24
forum: General Help
---

### Post by winaxter on 2008-06-24
hey guys,


ive got a hidden partition that i need to mount to ubuntu so i can access some files, its either sda1, sda2 or sda3 not sure lol..

im trying to mount it but i cant seem to.

can someone please help me by giving me a step by step instruction on how to do this please :confused:

---

### Post by VMC on 2008-06-24
> **winaxter said:**
> hey guys,


ive got a hidden partition that i need to mount to ubuntu so i can access some files, its either sda1, sda2 or sda3 not sure lol..

im trying to mount it but i cant seem to.

can someone please help me by giving me a step by step instruction on how to do this please :confused:

Can you output your file system so we can help. From Terminal type this:

```
sudo fdisk -l
```

---

### Post by winaxter on 2008-06-24
Device  Boot           Start          End         Blocks       Id      Systems
/dev/sda1              1              765         6144831      7    HPFS/NTFS
/dev/sda2 *            766            5214        35736592+    7    HPFS/NTFS
/dev/sda3              5215           9729        36266737+    7    HPFS/NTFS

---

### Post by bodhi.zazen on 2008-06-24
Which partition do you want to mount ? Temp or long term ?

If temp :

sudo mount -t ntfs-3g /dev/sda1 /mnt -o uid=1000,gid=100,umask=000

If that is not the partition you want, unmount it and mount another.

sudo umount /mnt

(only 1 n in umount)

---

### Post by winaxter on 2008-06-24
yeah its only temp just to see some files, when i type what you told me it replys with 

Mount: unknown filesystem type 'ntfs-3g'

---

### Post by bodhi.zazen on 2008-06-24
Ah,  use ntfs then. ntfs-3g = read write

ntfs = read only

---

### Post by winaxter on 2008-06-25
hey dude turns out it was fat32 so i changed the ntfs to vfat and it works exept the partition that i need to enter has superblock... it says 

Mount: /dev/sda1: Cant read superblock

---

### Post by winaxter on 2008-06-25
still not solved :( any1 got any ideas ??

---

### Post by bodhi.zazen on 2008-06-25
You can try :

```
sudo mount /dev/sda1 /mnt -o uid=1000,gid=100,umask=000
```

If you do not specify a file system mount will automatically select what it considers best.

The partition is listed as ntfs, you could get additional information with gparted or blkid

```
sudo blkid
```

---

### Post by winaxter on 2008-06-25
/dev/sda1: LABEL="" UUID="0159-6699" TYPE="vfat"
/dev/sda2: LABEL="ntfs"
/dev/sda3: LABEL="" UUID="963A-8102" TYPE="vfat"
/dev/evms/sda1: LABEL="" UUID="0159-6699" TYPE="vfat"
/dev/evms/sda2: LABEL="ntfs"
/dev/evms/sda3: LABEL="" UUID="963A-8102" TYPE="vfat"

---

