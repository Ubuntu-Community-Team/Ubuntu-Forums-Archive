---
title: "Shared Partition"
date: 2007-06-14
forum: General Help
---

### Post by KewL on 2007-06-14
Hey guys, I recently installed ubuntu and I had a question about partitioning. Currently I have a 200gig hardrive partitioned in two (one for xp one for ubuntu). I would like to create a 3rd partition which I can put all my music and movies that way they can be accessed from both os's. What would be the best way to set this up?

---

### Post by Blayde on 2007-06-14
[http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/) is handy for this kind of stuff. Just boot into gparted and you can resize your partitions and make a new one (probably fat32) for your files, but you should backup any important stuff first.

---

### Post by Graham1 on 2007-06-14
GParted (on the link above) is definately the way to go :). I have a similar setup between Ubuntu 7.04, Fedora 7 and openSUSE 10.2 accessing a shared FAT32 partition.

:)

---

