---
title: "deleting windows partition after install"
date: 2007-05-20
forum: General Help
---

### Post by Shardsofmetal on 2007-05-20
My setup right now is the following: a multiboot system with 3 options: Ubuntu, Windows XP, and Windows Vista. The Vista partition has 50 gigs, and I don't plan to use it ever again. So I want to delete the Vista partition, and give most of the space to Ubuntu, and some to XP. The XP partition is a primary one, and the Vista one, the main linux one, and the linux swap one currently reside on an extended partition. The Vista partition is the first one on the extended partition. So I want to delete the Vista partition, shrink the extended partition a little bit, expand the XP partition, and then give the rest of the space to linux. Unfortunately, the swap partition is in between the Vista and linux partitions, so i either have to slide it down after deleting Vista, or delete it and recreate it. 

So far, I haven't been able to do anything. I started gParted, and tried to unmount the Vista partition, but was unsuccessful. Where should I go from here? If I delete the Vista partition in Windows, how will I be able to resize the linux partition (I assume it will require unmounting)?

---

### Post by merlinus on 2007-05-20
I believe that you can boot from the Gparted live cd and do all these things, as none of the drives/partitions will be mounted.

You can download the .iso at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Good luck!

-merlin

---

