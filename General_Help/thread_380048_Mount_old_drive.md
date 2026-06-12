---
title: "Mount old drive"
date: 2007-03-09
forum: General Help
---

### Post by OOzypal on 2007-03-09
I have a hard drive that was corrupted previously and I had to reinstall Kubuntu from scratch. Since,  I was installing a new copy, I installed a bigger hard drive then installed Kubuntu on it. Now the old corrupted drive appears as 

```
/dev/sdb1
```

The drive does not get mounted automatically with the following line in fstab

```
/dev/sdb1  	/media/backup  	ext3  	rw,noauto,user,sync  	0 0
```

However mounting the drive manually works ok
```
sudo mount /dev/sdb1 /media/backup/
```

My question is how can I format the drive and mounted it  automatically?
Is it possible to make the two hard drive as one.

---

### Post by ArieT on 2007-03-09
I'm to very familiar with /etc/fstab but i think you should remove the 'noauto' option:
```
/dev/sdb1  	/media/backup  	ext3  	rw,user,sync  	0 0
```
Use mkfs for formatting this harddrive.

---

