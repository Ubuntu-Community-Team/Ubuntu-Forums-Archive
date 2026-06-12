---
title: "Can't get gutsy to mount hard drives at bootup"
date: 2008-02-25
forum: General Help
---

### Post by msarro on 2008-02-25
Ok, did gutsy change how drives have to be mounted? I have 2 hard disks beyond the OS hard disk. I can doubleclick them in the "Computer" menu to mount them with no issue. However I can't get gutsy to mount them at bootup.

At the moment I have them added as such in fstab:

```
[mounted stuff cut out]
/dev/sdb /media/disk-1  ext3  defaults  0  0
/dev/sda /media/disk-2  ext3  defaults  0  0
```

Upon running mount -a I get the following error for each drive:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

mount: wrong fs type, bad option, bad superblock on /dev/sda, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so
```

What am I missing? That used to be enough to mount a drive if I remember correctly. Whats this UUID stuff I see now? Does it matter that my main drive is SATA and the 2 secondary are IDE?

---

### Post by msarro on 2008-02-25
bump for great justice

---

### Post by taurus on 2008-02-25
Shouldn't they be something like /dev/sda1 & /dev/sdb1 instead of just /dev/sda & /dev/sdb?

```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2008-02-25
sda = entire hard drive

sdb = entire hard drive

You need a number, like sda1 or sdb1

To lest your partitions:

```
sudo fdisk -l
```

Basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

fstab : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by msarro on 2008-02-25
Dangit, I knew it was something stupid :) Thanks much!!!! Working like a charm now!
been ages since I had to play with fstab and the UUID thing with my main drive kinda threw me off. Oh well.

---

