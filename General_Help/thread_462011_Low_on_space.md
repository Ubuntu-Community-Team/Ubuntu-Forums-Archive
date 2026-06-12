---
title: "Low on space"
date: 2007-06-02
forum: General Help
---

### Post by erusfatum on 2007-06-02
hey guys! i installed ubuntu on a 10gb partition with dual-boot windows, just to check it out and play around,  but after a while i got fascinated with it, but now i just realized ive got left 1.4 gb free space. Can i resize the windows partition to give its free space to ubuntus partition? is there a safe way? i had tragic experience with partitions when both linux and windows couldt boot...

---

### Post by Lord Illidan on 2007-06-02
Yes, you can resize windows partitions. Do it from the live cd preferably. There is an option under System -> Administration -> Gparted. You can now resize windows partitions.

I never lost data, but then you never know what can happen. Thus, be sure to defragment the disk, and also, make sure you take a backup. Then you can create another partition in the free space.

Sadly, I dunno how to grow a partition. Gparted only seems to decrease it.

Of course, you can get a new harddisk on the cheap.

---

### Post by taurus on 2007-06-02
GParted LiveCD should be able to decrease your Windows partition and merge that space to your Linux partition.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

