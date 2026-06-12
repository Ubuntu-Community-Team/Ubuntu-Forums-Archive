---
title: "Lost ext3 FS and I am FSKED"
date: 2007-02-09
forum: General Help
---

### Post by digger4ubuntu on 2007-02-09
Hello all,

I am having a bad day.  I have a 250GB drive that I had setup for multiple distro's.  The partitions were as follows:

```
/dev/sda1       (k)ubuntu root
/dev/sda2       extended
/dev/sda3       debian/ubuntu/etc root (my distro testing parition)
/dev/sda5       swap
/dev/sda6       /home
```

I had upgraded my sda1 kubuntu partition to edgy and was starting to have issues so I wanted to have dapper on sda3.  Well in the wonderful world of multitasking I fscked up and missed the "reformat" checkbox on my /home partition during the dapper install.  (This will be the last time I ever use the live-cd gui install)  I saw "formatting /dev/sda6" pop up during the install but I could not kill it fast enough.

It looks like recovering via a back superblock is not going to be a viable option:

```
root@hermes:~# for i in `dumpe2fs /dev/sda6 | grep Backup | awk '{print $4}' | sed s/\,// | grep -v dump`; do e2fsck -B $i -n /dev/sda6
> done
dumpe2fs 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
e2fsck 1.39 (29-May-2006)
/dev/sda6: clean, 11/19660800 files, 616967/39321087 blocks
root@hermes:~#    
```

Does anyone have any tricks/ideas on what I can do?  There was a lot of data (80GB+) on there I need and I hope I/someone can find a way to get it back.

-D

---

### Post by digger4ubuntu on 2007-02-09
BUMP

Offering rewards, slave labor, etc.

---

### Post by digger4ubuntu on 2007-02-12
I am getting closer and closer with Photorec.  Does anyone know the default block size used in Dapper for a 150GB EXT3 /home file system?  I believe it is 4kb but want to make sure.

---

### Post by esaym on 2007-02-12
Dang sorry to hear this.  It is ANYONES worst nightmare

---

