---
title: "Showing icons on desktop"
date: 2007-01-28
forum: General Help
---

### Post by daz4126 on 2007-01-28
Hi,

When I boot into Ubuntu, My external hard drive shows up as an icon as well as all the partitions on my main hard drive. I found out that if I go into configuration editor and then choose apps -> nautilus -> desktop I could check or uncheck the box that says 'volumes_visible', but this is an all or nothing option.

Does anybody know if it is possible to choose which volumes are visible, becaue I would like to see my external usb hard drive, but not the internal partitions on the desktop.

Thanks,

DAZ

---

### Post by taurus on 2007-01-28
Instead of mounting your harddrive to /media/xxx in /etc/fstab, mount it to /mnt/xxx and it won't show up on your desktop.

---

### Post by daz4126 on 2007-01-28
Thanks taurus, I edited fstab and now only the external drives appear on the desktop, but I can't find the internal drives anywhere - where should I be looking?

thanks again,

DAZ

---

### Post by taurus on 2007-01-28
If you deleted an entry from /etc/fstab, then it is not mount so you need to mount it by hand.  Tell me which one you want to mount from the output of this command?

```
sudo fdisk -l
```

---

### Post by daz4126 on 2007-01-28
Okay this is the output:

```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6399    51399936    7  HPFS/NTFS
/dev/hda2           12749       24043    90727087+   c  W95 FAT32 (LBA)
/dev/hda3            6400       12748    50998342+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1165     9357831   83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb3            1166        2330     9357862+  83  Linux
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6527    52428096    b  W95 FAT32
/dev/sda2            6528       13054    52428127+   b  W95 FAT32
/dev/sda3           13055       19457    51432097+   b  W95 FAT32

```

hda is my internal hard drive with windows on.
hdb has ubuntu on.
sda1,2,3 are the external drives partitions.

I didn't delete anything from fstab, just changed hda to /mnt/hda1 etc..

thanks,

DAZ

---

### Post by taurus on 2007-01-28
And did you remember to create /mnt/hda1?  

```
sudo mkdir /mnt/hda1
sudo mount -a
df -h
```

---

### Post by daz4126 on 2007-01-28
> **taurus said:**
> And did you remember to create /mnt/hda1?  

```
sudo mkdir /mnt/hda1
sudo mount -a
df -h
```


Nope! Didn't have a clue that's what I had to do! Now it seems to work fine. Will those files always be in mnt every time I boot up from now on?

Thanks for all the hand-holding Taurus, it is much appreciated.

DAZ

---

### Post by taurus on 2007-01-28
If they are in /etc/fstab, then they will always be where they should be when you boot Ubuntu.  Reboot and see what happens.

---

### Post by daz4126 on 2007-01-28
great, thanks.

Just to clear up: 'they will always be there..' but.... I have to create that folder first - fstab will not creat folders for me, is that right?

---

### Post by ynnhoj on 2007-01-28
this is correct; you need to create the directory before you're able to mount something to it.

---

### Post by taurus on 2007-01-28
> **daz4126 said:**
> great, thanks.

Just to clear up: 'they will always be there..' but.... I have to create that folder first - fstab will not creat folders for me, is that right?

You only have to create it once and that's it.

---

