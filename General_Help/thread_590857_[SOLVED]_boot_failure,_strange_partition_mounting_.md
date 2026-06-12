---
title: "[SOLVED] boot failure, strange partition mounting behavior"
date: 2007-10-25
forum: General Help
---

### Post by oznozz on 2007-10-25
I began to notice a serious problem earlier today when I was trying to boot into Ubuntu and it would not boot further than the login screen without any login boxes.  This is true in recovery mode as well.  I have subsequently tried to back up my home directory with ext2ifs under windows and failing that, I have tried to use KNOPPIX to figure out what is happening.

I don't have an up to date enough backup and google wasn't helpful, so here I am.

The current situation is this :

I have four partitions on an HP laptop.

/dev/hda1  Windows XP Tablet Edition
/dev/hda2  Ext2/3 home directory which also serves as My Documents
/dev/hda3  Ubuntu
/dev/hda4  Swap

I have fully upgraded Ubuntu 7.04 (I think that is the correct number).

When I execute the following commands (left) in KNOPPIX 5.1.1, I get the following behavior (right) :

click on hda2 icon   -   explorer window crashes

$ sudo mount /dev/hda2/ /media/hda2   -  seems to work

$ ls /media/hda2  -  seems to work

$ ls -a /media/hda2  -  seems to work

$ ls -a /media/hda2/Recycled  - seems to work

$ ls /media/hda2/agh9a  {my home dir}  -  command prompt never returns!  program hangs!

$ ls /media/hda2/agh9a/tmp  -  ls crashes with a segmentation fault!  (non replicable)

$ sudo ls /media/hda2/agh9a  {my home dir}  -  command prompt never returns!  program hangs!

$ sudo ls /media/hda2/agh9a/tmp  - command prompt never returns!  program hangs!

$ sudo fsck /dev/hda2  -- no errors

$ sudo e2fsck /dev/hda2 -- no errors



What should I try that I have not tried?

Thanks

---

### Post by nacho32 on 2007-10-25
I would suggest the[ super grub boot loader]("http://www.linux.com/articles/57240")

---

### Post by oznozz on 2007-10-25
To summarize :

I had a problem where an ext2/3 filesystem appeared to be in good health, but using basic tools such as cp or ls caused crashes and hangs by those programs.

Problem :

The filesystem on the partition had been marked clean and healthy when in fact it was broken.

This means that unless a file system checker was forced to check the system, it would say everything was fine, although that was false.

More technically, the htree directory contained an invalid root node.

Solution :

a simple 

$ sudo e2fsck -f /dev/hda2

under KNOPPIX forced a check, found the bad inode and then fixed it when I said "yes" clear the htree.

---

### Post by greenstar on 2007-10-25
Please mark this thread as solved so others may benefit from your experience. Instructions are in my signature. The [SOLVED] button is in the thread tools menu at the top of the thread.:)

Thanks,
Greenstar

---

### Post by oznozz on 2007-10-26
Thanks Greenstar.  I know more Debian/Ubuntu than Forum!

I realized that I failed to explain what I think an htree does and why it's ok to blast a bad one, since google searching was not immediately helpful in my experience and I was hesitant to answer "yes" given that all my lovely data could potentially rely on said htree for all I knew at the time.

An htree seems to be an ext filesystem enhancement that allows ext to perform faster by hashing directories.  Blowing away the htree will not adversely affect the data in the filesystem, although it might temporarily slow down filesystem access for a bit.

That seriously glosses over the details.  See 

[http://portal.acm.org/citation.cfm?id=1268488.1268508&coll=&dl=&CFID=15151515&CFTOKEN=6184618](http://portal.acm.org/citation.cfm?id=1268488.1268508&coll=&dl=&CFID=15151515&CFTOKEN=6184618)

[http://www.nongnu.org/ext2-doc/ext2.html#CONTRIB-PERFORMANCE](http://www.nongnu.org/ext2-doc/ext2.html#CONTRIB-PERFORMANCE)

---

### Post by greenstar on 2007-10-26
Thanks for filling us in on the problem & solution. Every contribution & contributor make Ubuntu a little better than it was without them. :)

Thanks again,
Greenstar

---

