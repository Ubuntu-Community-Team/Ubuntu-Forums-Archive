---
title: "resized root, cannot boot"
date: 2008-02-10
forum: General Help
---

### Post by spartan777 on 2008-02-10
ha, that rhymed.

so i deleted a secondary storage partition on my harddrive, then resized my root partition to take up the empty space using a livecd and gparted. now when i try to boot, i see ubuntu load about 1/3 of the way, then it drops into the command line, and i get the following;

```
Log of fsck -C -R -A -a 
Sun Feb 10 05:59:47 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Unable to resolve 'UUID=0c6af15a-2093-4bce-bdf3-11adece34d2c'
/dev/sda5: clean, 8610/49840128 files, 47177894/49815549 blocks (check in 5 mounts)
fsck died with exit status 8

Sun Feb 10 05:59:47 2008
----------------

```

what do i need to do? this seems to be an issue with my fstab config file, but i don't know where to go from there. thanks for the help in advance.

---

### Post by em3raldxiii on 2008-02-10
Hmm, not entirely sure, but since no one else has posted in 10 minutes, I will throw a suggestion out there ...

Is it possible that FSCK is looking for the partition that no longer exists?  perhaps this UUID that you posted is the one for that particular partition.  Perhaps if you commented out (put a # in front) the line in your fstab file?

I believe you can use your live disc to access the fstab file to fix it.

---

### Post by spartan777 on 2008-02-10
thanks so much, it worked perfectly. i probably should have known that, but i'm a bit rusty on my linux knowledge.

---

### Post by em3raldxiii on 2008-02-10
No problem!  I am a bit rusty with that stuff too ... had to scour the deep and corroded recesses of my subconsious for that one ;) LOL ...

---

