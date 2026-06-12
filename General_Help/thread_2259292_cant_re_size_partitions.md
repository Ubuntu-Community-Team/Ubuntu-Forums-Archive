---
title: "cant re size partitions"
date: 2015-01-03
forum: General Help
---

### Post by Louis_Levene on 2015-01-03
hello, i have an issue with gparted when i try and shrink my ubuntu partition to make some room for windows
the minimum and maximum size are exactly the same, so i cant shrink or grow when i know it is no where close to being full, i am also running from a live usb so it is unmounted... here is a screenshot
[http://i.imgur.com/cv1EwOd.png](http://i.imgur.com/cv1EwOd.png)
any help would be awesome!

---

### Post by Bucky Ball on 2015-01-03
*Thread moved to **General Help**.*

Looks like an LVM partition. I don't know much about them, but from what I've gathered, gparted cannot resize them. I believe they can be resized, though, using a terminal.

Hopefully someone in the know can leap in soon to expand on that. Good luck. ;)

PS: I also found this [here]("http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume"):

> Use GParted to resize the LVM physical volume. GParted won't let you shrink the LVM physical volume to a size smaller than what the unallocated space allows.

Maybe it's something to do with this. Expanding is fine but shrinking not. :-k

---

### Post by Louis_Levene on 2015-01-03
ok thanks ill look into that link

---

