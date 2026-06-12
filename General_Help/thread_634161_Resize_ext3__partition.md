---
title: "Resize ext3 / partition"
date: 2007-12-07
forum: General Help
---

### Post by tienlex on 2007-12-07
Hi everyone,
As you can see in my attachment, I have an HP laptop with 160GB HDD and I've install Ubuntu 7.10 with Windows Vista, I installed Ubuntu on 20GB partition but now I'm very like and feel comfortable with this OS so I want to resize its partition larger then can install more applications.

/dev/sda1 is Windows patition (C:\)
/dev/sda2  is my data driver (Z:\) in Windows
/dev/sda3 is HP_RECOVERY patition
/dev/sda4 is extended partition
/dev/sda5 is ext3 / partition
/dev/sda6 is swap

I've shrink /dev/sda2  to get  15.4GB unallocated partition. But my problem here is how to enlarge Ubuntu partition to use unallocated partition because i always get this message from Gparted : "I is not possible to create more than 4 primary partitions"
I don't want to reinstall or lost any data I had.


Thanks,
TLE

---

### Post by Ramorous on 2007-12-07
I would recommend booting off a Live CD so that the root partition is not mounted and then just use gparted to resize.

** Do backup your stuff first ** (you never know what could happen)

---

### Post by forestpixie on 2007-12-07
will gparted resize a partition 'inside' an extended partition to include space outside it

---

### Post by Ramorous on 2007-12-07
I would like to say yes, but I've never tried. There might be something out there in the google world to help you, but I personally don't think this is possible.

What I would recommend at this stage, if you'd like to make your machine 100% linux. Create a temporary partition with that 15G, copy over your etc, home and other personalized files over to that directory and simply re-install Ubuntu while re-partitioning all drives (including your swap).

---

### Post by Ramorous on 2007-12-07
You may want to boot from a live CD, unmount the swap and other partitions in the extended and try expanding the extended partition then expand the one within it. That's where I'd start.

---

### Post by forestpixie on 2007-12-07
I've had a look at the documentation for gparted and it is possible, although you might find it easier if you download the livecd version and boot from it.

Try the ubunut livecd first - although it's probable quicker to download and burn the gparted cd - depending on your ram and see what you can do with it.

see this [http://ubuntuforums.org/showthread.php?t=633663](http://ubuntuforums.org/showthread.php?t=633663)

---

