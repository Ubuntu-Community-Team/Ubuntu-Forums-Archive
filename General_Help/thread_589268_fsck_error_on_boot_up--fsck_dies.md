---
title: "fsck error on boot up--fsck dies"
date: 2007-10-24
forum: General Help
---

### Post by herbster on 2007-10-24
```
Log of fsck -C -R -A -a 
Tue Oct 23 23:08:07 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: No such file or directory while trying to open /dev/sdc1

/dev/sdc1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/sdc2

/dev/sdc2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/sdc3

/dev/sdc3: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sdb3: clean, 120834/33964032 files, 51344711/67902738 blocks
/dev/sda3: clean, 132554/2621440 files, 1230429/5237190 blocks
/dev/sdb1: clean, 132342/3204992 files, 1366179/6399894 blocks
/dev/sda4: clean, 182726/34734080 files, 57134467/69438954 blocks
/dev/sdb2: clean, 163484/1921984 files, 1540165/3839527 blocks
fsck died with exit status 8

Tue Oct 23 23:08:08 2007
----------------
```

At the shell I can hit CONTROL+D and it then continues into Ubuntu just fine, but what 's going on? /dev/sdc* = my external hd. It did this even after I powered off the enclosure.

---

### Post by herbster on 2007-10-24
Okay I thought it was my external hd causing issues but it's not even plugged in and I just started GParted, it's taking a longggg time "scanning devices" at the start before it shows everything. What the hell is going on?? I know I have to do something here but I'm not sure what.

---

