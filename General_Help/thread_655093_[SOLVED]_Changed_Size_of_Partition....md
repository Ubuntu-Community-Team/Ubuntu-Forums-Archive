---
title: "[SOLVED] Changed Size of Partition..."
date: 2007-12-31
forum: General Help
---

### Post by kryth on 2007-12-31
I changed the Size of my ubuntu  Partition from 4gb to 7gb with Gparted ...but ubunutu only sees the partition as 4gb still.  Anyone know what's going on here? Any help? Or clues thanks.

---

### Post by taurus on 2007-12-31
Can you post a screenshot of gparted, showing your harddrive?

---

### Post by kryth on 2007-12-31
err....sure as soon as I find somewhere to host the image.

---

### Post by kryth on 2007-12-31
[http://myfreefilehosting.com/f/14c4694faa_0.12MB](http://myfreefilehosting.com/f/14c4694faa_0.12MB)

---

### Post by kryth on 2007-12-31
or
[http://bayimg.com/aaIfDaaBk](http://bayimg.com/aaIfDaaBk)

P.S. Don't laugh to0 hard about the 2gb swap.

---

### Post by taurus on 2007-12-31
Can you post the output of this command?

```
df -h
```

---

### Post by RC Howe on 2007-12-31
How could you have used 6 gigabytes of space on that partition when you only had four previously?

---

### Post by kryth on 2007-12-31
> **RC Howe said:**
> How could you have used 6 gigabytes of space on that partition when you only had four previously?

Be damned if I know.


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.7G  4.4G   49M  99% /
varrun               1013M   96K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   92K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0             163M  163M     0 100% /media/cdrom0

---

### Post by taurus on 2007-12-31
Did you increase the size of /dev/sda5 with gparted from the LiveCD?

---

### Post by kryth on 2007-12-31
RC Howe....Oh.....I gparted this a month ago.....I only realized the difference in size once I started up my BT habit and got disk full error.

---

### Post by kryth on 2007-12-31
Yeah......from the live cd.

---

### Post by kryth on 2007-12-31
Damn, I have an idea ......I backed up system with partimage before using Gparted.......changed stuff with Gparted.........everything fine for a few week....then I screwed up compiz or something....then restored the back up.......probably the problem...right?

---

### Post by taurus on 2007-12-31
What does your /etc/fstab look like anyway?

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by kryth on 2007-12-31
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=41f02cb6-d821-4226-904f-f1e294e5d929 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=a6ef89d0-84b9-4fdc-84b2-6047710277df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2              14         673     5295104    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1956       19457   140584815    7  HPFS/NTFS
/dev/sda4             674        1955    10297665    5  Extended
/dev/sda5   *         674        1700     8249346   83  Linux
/dev/sda6            1701        1955     2048256   82  Linux swap / Solaris

---

### Post by kryth on 2007-12-31
I guess I broke it good.

---

### Post by dcstar on 2007-12-31
> **kryth said:**
> 
.........
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2              14         673     5295104    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1956       19457   140584815    7  HPFS/NTFS
/dev/sda4             674        1955    10297665    5  Extended
/dev/sda5   *         674        1700     **8249346**   83  Linux
/dev/sda6            1701        1955     2048256   82  Linux swap / Solaris

/dev/sda5 is a 4G partition, if you want it bigger you need to remove the (probably useless) swap partition and then extend it into the free space using the Ubuntu Live CD.

It would probably be better to reduce the massive sda3 NTFS partition and then increase the size of the Extended partition and then increase /dev/sda5 in that.

---

### Post by kryth on 2008-01-01
Okay, fixed it. I used Gparted again from live CD. I decrease swap and increase linux partition. And that fixed it. Thanks for the help.

---

