---
title: "repartition"
date: 2007-05-06
forum: General Help
---

### Post by dpar on 2007-05-06
When I boot Feisty, it has an icon on the desktop for another partition with an old ubuntu install that no longer works. (My experimental version:) ) If I reformat that partition, will it screw anything up in my Feisty. Or will Feisty just automaticly ignore the empty partition?

---

### Post by seshomaru samma on 2007-05-06
probably wont hram ,but if you want to be on the safe side - post the output of
```
sudo fdisk -l
```

(if you do format ,you will need to mount the new partition- like [this]("http://www.psychocats.net/ubuntu/mountlinux"))

---

### Post by dpar on 2007-05-06
Hi, thanks. Heres the output of fdisk -l.

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9070    72854743+  83  Linux
/dev/hdd2            9071       14593    44363497+   5  Extended
/dev/hdd5           14217       14593     3028221   82  Linux swap / Solaris
/dev/hdd6            9071       14216    41335182   83  Linux

hdd6 is the one I was going to reformat.

---

### Post by seshomaru samma on 2007-05-06
looks ok
are you going to use Gparted?
format as ext3?

---

### Post by dpar on 2007-05-06
Yeah, it's always worked well for me before. I just wanted to make sure because I finally got my wife convinced to switch completely to ubuntu and I didn't want to wreck the Fiesty that I use all the time.

Thanks very much for your help.

---

