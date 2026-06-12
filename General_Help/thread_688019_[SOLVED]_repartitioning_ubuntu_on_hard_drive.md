---
title: "[SOLVED] repartitioning ubuntu on hard drive"
date: 2008-02-04
forum: General Help
---

### Post by The Saint on 2008-02-04
Hi, I have installed ubuntu on my laptop which was already running XP ( where most of my work is kept. My hard drive capacity is 160GB. My plan was to allocate 40GB to ubuntu and 120GB to xp. I however ended up doing the reverse, and giving 120GB to ubuntu and 40 to xp. My work and data on xp hence has become severly affected. :(  How do I go about reallocating some of the hard drive safely back to xp:confused:

Thanks Guys

---

### Post by shutslar on 2008-02-04
use gparted to shrink your ubuntu partitions closer to the end of the drive...leaving a freespace gap between windows and ubuntu...then use gparted to extend your windows partition into this free space.  You should be able to just drag the graphic representations to do this.

---

### Post by The Saint on 2008-02-04
Hi Shutslar

When I tried it through ubuntu all the ubuntu partitions appeared with a lock sign on it ,:mad:and it would not allow me to change the partition sizes!!!
Help :confused:

---

### Post by mauijohn on 2008-02-05
I have been using a CD of the puppy distro to play around with different size partitions for XP, debian, and ubuntu. puppy has gparted and the distro is fairly small and it's a great CD to have for situations like this.

---

### Post by The Saint on 2008-02-05
> **mauijohn said:**
> I have been using a CD of the puppy distro to play around with different size partitions for XP, debian, and ubuntu. puppy has gparted and the distro is fairly small and it's a great CD to have for situations like this.


It works like a dream. Thanks. I guess the trick is to use a live cd with gparted on it, instead of trying to use the gparted loaded on the hard drive.

---

