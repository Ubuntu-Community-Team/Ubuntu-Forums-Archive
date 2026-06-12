---
title: "Moving Partitions...."
date: 2007-11-24
forum: General Help
---

### Post by tomcullpepper on 2007-11-24
So my HD is currently partitioned like this...


|OMG VISTA 140GB|FREE SPACE FOR VISTA 100GB|LINUX 17GB| RECOVERY 4GB|EMPTY SPACE 4GB|

I want to make Linux expand into that empty space, and or remove the recovery partition all together, it does nothing but keeps replaceable files......  Kinda useless really, if a total crash ever happened, I would still have to call HP, then Windows.

---

### Post by public_void on 2007-11-24
Try [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/"), its a bootable Linux CD with [GParted]("http://gparted.sourceforge.net/"). It will allow you to remove the recovery partition and expand the Linux partition into the empty space.

---

### Post by tomcullpepper on 2007-11-24
What if I don't want to reinstall Linux, I like my current release, I just need more room...

---

### Post by skymera on 2007-11-24
nono

live cd dosent reinstall :)

---

### Post by kaiju on 2007-11-24
> What if I don't want to reinstall Linux, I like my current release, I just need more room...

as public_void already said, you can boot from the gparted livecd, remove the unneeded partition and expand the one with your linux on it. you really don't need to reinstall anything.

---

