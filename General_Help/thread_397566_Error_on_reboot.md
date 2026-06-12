---
title: "Error on reboot"
date: 2007-03-30
forum: General Help
---

### Post by Master Shake on 2007-03-30
A while back I tried installing another variant of Linux on my system, so I could triple boot XP, Ubuntu and whatever the linux was (I forgot at this point).

Anyway, the install didnt take, so I had to resize my partitions.  Now when I boot into linux, the var/logs/fsck log shows this:
```

Log of fsck -C -R -A -a 
Fri Mar 30 18:22:20 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda6

/dev/hda6: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Fri Mar 30 18:22:20 2007
```

ANy ideas on how to solve?

---

### Post by jerryrw on 2007-03-30
Was the other disro SUSE?  It may be a reiser file system.

---

### Post by Master Shake on 2007-03-31
Nah..  It was a version of slackware.....

Anyone?

---

