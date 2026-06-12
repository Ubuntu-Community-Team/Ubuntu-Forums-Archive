---
title: "[SOLVED] mdadm doesn't mounts md0 but not md1"
date: 2007-05-08
forum: General Help
---

### Post by pieroxy on 2007-05-08
Hi,

I have two raid devices (md0 and md1). Here is what my mdadm.conf looks like:

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=3d1b9ed9:6af17dbe:bc61d10c:c5df0133
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=eb064cd3:a767ec50:76f14d9c:14653191

Since I upgraded to feisty, md0 always mounts fine. Sometimes md1 is mounted, sometimes not and I get a maintenance shell at boot time. md1 is made out of 2 sata drives. md0 is one PATA disk (the other one failed I am running on 1 drive for now)

Since today (3 days after upgrade) md1 doesn't mount anymore at all. no matter what I do I can't get /dev/md1 to appear (actually /dev/md1 is there but not assembled so I can't do anything with it). Here is the relevant portion of my dmesg:


[   67.189492] md: md0 stopped.
[   67.374258] md: bind<hde1>
[   67.441878] md: raid1 personality registered for level 1
[   67.445330] raid1: raid set md0 active with 1 out of 2 mirrors
[   67.446518] md: md1 stopped.
[   72.969053] eth0: no IPv6 routers present
[   86.934556] NTFS driver 2.1.28 [Flags: R/O MODULE].
etc...

cat /proc/mdstat:

Personalities : [raid1] 
md0 : active raid1 hde1[0]
      117218176 blocks [2/1] [U_]
      
unused devices: <none>


(md0 is running on 1 drive at this time). md1 is stopped. What I did yesterday is a dpkg-reconfigure to define none of my arrays needed for / because that was causing a busybox shell at boot time way too often.

Any help? Any hints?

Thanks

---

### Post by pieroxy on 2007-05-08
I got that one as well. It looks as if the array identification by UUID doesn't quite work on my system. Here is the new mdadm.conf that I use now (and it works) :
```

DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid1 num-devices=2 devices=/dev/sda1,/dev/sdb1
DEVICE /dev/hde1 /dev/hdg1
ARRAY /dev/md1 level=raid1 num-devices=2 devices=/dev/hde1,/dev/hdg1

MAILADDR root
```


Go figure ...

---

