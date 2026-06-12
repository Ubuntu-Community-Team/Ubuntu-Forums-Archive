---
title: "Is this HD dead?"
date: 2016-02-12
forum: General Help
---

### Post by Evil Wayz on 2016-02-12
Gave a tower to a friend, pulled the drive that wzs in it out first.  Haven't used it for five years, was curious to see what was on it.  THis is the output when it tries to mount:

```
Error mounting /dev/sdd1 at /media/wolf/dc6ffa6f-98a6-478d-8d74-80369625690e: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdd1" "/media/wolf/dc6ffa6f-98a6-478d-8d74-80369625690e"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

IS it dead or could I possibly mount it read only?

---

### Post by buzzingrobot on 2016-02-12
One thing I notice is it reported the wrong file system type when you tried to mount it as ext4. 

Have you tried deleting any existing partitions on the drive, then repartitioning and formatting it?

---

### Post by pqwoerituytrueiwoq on 2016-02-12
install [gsmartcontrol]("apt:gsmartcontrol") and see what it says and run a smart test on it
make sure your cable is fully seated, i had the one on my ssd crooked and was getting some strange stuff - [http://ubuntuforums.org/showthread.php?t=2287341]("http://ubuntuforums.org/showthread.php?t=2287341")
try using gparted to check and repair the partition

---

### Post by kurt18947 on 2016-02-13
If in doubt, don't use it for anything critical until it proves reliable. Use it for things like web browsing or office type stuff where data files are duplicated elsewhere. I had an 80 GB. W.D. drive that would fail in no pattern that I could discern, it'd be perfect for weeks or months then lose its mind. I assume it had some sort of intermittent controller problem or something similar. Maybe try a different cable?

---

### Post by Evil Wayz on 2016-02-21
I tok a look at it in gparted and it's showing nothing is on there now. But it won't let me create a new partition.  Gives me varios I/O errorsI believe it's dead.

---

### Post by ik-0 on 2016-02-21
I don't want to sound condescending but did you run gparted as root?

---

