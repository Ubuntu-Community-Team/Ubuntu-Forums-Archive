---
title: "[solved]/dev/sdc2 not appearing"
date: 2007-12-11
forum: General Help
---

### Post by Aseld on 2007-12-11
I'm trying to install KNOPPIX on my thumb drive - I'm doing it from Ubuntu, and I need to do a mkfs.ext2 on the second partition. However the command

```
 sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sdc2
```

gives me the error

```
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/sdc2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```

ls /dev | grep sdc outputs sdc and sdc1, but no sdc2. The partition has definitely been created - it shows up when I do fdisk -l. 

What am I doing wrong here? How do I get /dev/sdc2 to appear?

Thanks a lot.

Edit: Sorry, solved my own problem yet again. I needed to take the drive out and plug it back in again.

---

