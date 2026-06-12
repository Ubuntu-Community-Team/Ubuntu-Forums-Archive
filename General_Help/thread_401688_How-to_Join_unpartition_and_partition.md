---
title: "How-to Join unpartition and partition"
date: 2007-04-04
forum: General Help
---

### Post by ajmorris on 2007-04-04
Hi, 
I have just deleted my windows partition.  WOO-HOO i finally switched to a windows free life. \\:D/ 
I want to re-assign that unallocated space back into my reiserfs partition. I have tried to do this in gparted and couldn't find a way to do it. (on the ubuntu live cd). Can i do it in this app?; if not what app can i use? or can i do it through CLI? Also i have tried the knoppix live cd with qparted and still no luck. Please help i don't want or need 2 partitions.

---

### Post by m.musashi on 2007-04-04
> **ajmorris said:**
> Hi, 
I have just deleted my windows partition.  WOO-HOO i finally switched to a windows free life. \\:D/ 
I want to re-assign that unallocated space back into my reiserfs partition. I have tried to do this in gparted and couldn't find a way to do it. (on the ubuntu live cd). Can i do it in this app?; if not what app can i use? or can i do it through CLI? Also i have tried the knoppix live cd with qparted and still no luck. Please help i don't want or need to partitions.

I'm not sure you can actually do this. I think you can delete the partition you don't need and then resize your ubuntu partition but I know I have never been able to move a partition. If you want to move "to the left" so to speak in gparted I think you will not be able to. There may be apps that will do this but I don't know of any. You might consider making the ex-windows partition your /home for example (if you don't already have a separate /home) or some other form of storage. Otherwise you might have to reformat and reinstall to be able to use the whole drive as one partition. Again, there may be a way but I've not found one.

---

### Post by ajmorris on 2007-04-04
i found something that does it: "resize_reiserfs" which comes with the "reiserfsprogs" package. Only problem is the reiserfs partition that i want to resize has to be unmounted and i don't know how to get that program from the repos onto a floppy so i can resize my only reiserfs partition.

---

### Post by m.musashi on 2007-04-04
Your best bet is to find something on a live Cd that will work. You can't unmount the partition that you boot. Something like knoppix might work. Don't know if that particular package is on it though.

---

### Post by zvacet on 2007-04-05
Download Gparted live CD.[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
Just resize your existing partition to unallocated space.

---

### Post by The Pinny Parlour on 2007-04-05
Try gparted
```
sudo apt-get install gparted

```

---

### Post by m.musashi on 2007-04-05
> **zvacet said:**
> Download Gparted live CD.[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
Just resize your existing partition to unallocated space.

If I remember correctly, gparted will not let you "move" a partition which it what you will have to do if windows was the first partition and you want to move Ubuntu towards the "front". I just tried to do something similar. I wanted to shrink windows and move Ubuntu to fill the gap. I couldn't get it to work and ended up making a separate partition there for storage.

If you do get it to work please share as I'd like to know.

---

### Post by ajmorris on 2007-04-05
gparted allows you to resize a reiserfs partition but only if the unallocated space is after the reiserfs partition, not before. My problem was i couldn't move the unallocated space to after the partition.

---

