---
title: "Making images from partitions"
date: 2008-02-24
forum: General Help
---

### Post by Zalbor on 2008-02-24
Is there a program I can use to make a (compressed or not, it's not important) image of a hard drive partition? For windows I use Norton Ghost, I'm looking for something that does a similar thing.
Since the partition I'm interested in using it on is not so big (it could easily fit into a dvd) compression is not important, although it would be good.

I suppose I could use the terminal program dd to do it, with the right options. But maybe there's an easier way.

---

### Post by geo909 on 2008-02-24
Clonezilla live is *exactly* what you are looking for. 
[http://clonezilla.sourceforge.net/]("http://clonezilla.sourceforge.net/")
It's very easy to use (you boot it as a live CD) and supports many formats (incl. NTFS,vfat). You can also save entire disks
(even if you have multiple partitions in different formats). The good thing with it is that the image only takes the size of the occupied space of the disk. A 500GB image with 5 GB occupied will make a 5GB image. It also supports many levels of compression and it's really fast (It took me 20 minutes for an 80 GB disk , NTFS/ext3/fat/swap partitioned).

dd will make an image of the exact size of the partition no matter how much space is occupied.
It is also very slow related to clonezilla.

---

### Post by gambothell on 2008-02-24
If you have a Windows machine, buy Acronis True Image version 11 - which you can download from Acronis.com. When you install it, burn the recovery CD. You can then boot your Ubuntu machine from the Acronis recovery CD and backup your ext3 partition. It has saved my butt many times and is worth every dime.

---

### Post by Zalbor on 2008-02-24
:thumb: Thanks for your replies!

---

### Post by noynac on 2008-02-24
Please delete

---

