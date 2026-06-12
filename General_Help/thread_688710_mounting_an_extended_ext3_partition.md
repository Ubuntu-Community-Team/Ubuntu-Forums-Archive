---
title: "mounting an extended ext3 partition"
date: 2008-02-05
forum: General Help
---

### Post by Tristanm1 on 2008-02-05
I have created an ext3 partition inside my extended partition. The only problem is, I can't mount it. At the moment I am booting off of the Ubuntu Gutsy live cd to do all the work. according to the live cd, it can't be mounted as it is not in the fstab, which looks like this:

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

the partition, according to the partition editor, is /dev/sda6

How do I mount it?

---

### Post by Zwack on 2008-02-05
try

sudo mount /dev/sda6 /mnt 

Presuming that /mnt already exists your new partition will be mounted there...

Z.

---

### Post by Tristanm1 on 2008-02-05
Alright, next question.

This is part of my moving my /home partition from a primary to an extended partition. I am making room for some other things. How do I change my settings so that it mounts /dev/sda6 as home instead of /dev/sda3? here is the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=50eddaec-6fd2-4497-a1b3-d70ccb0cf9f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=8d656b4e-a839-444e-9b1e-2da37328a6e4 /home           ext3    defaults        0       2
# /dev/sda5
UUID=f2fea748-a232-47d4-b455-da71843e55eb none            swap    sw              0       0
```

I assume I change the part commented as /dev/sda3, but it's the UUID that trips me up as I have no clue how to find that.

---

### Post by bodhi.zazen on 2008-02-05
If you are wanting to move /home, better follow a guide ;)

Psychocats : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

