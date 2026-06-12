---
title: "Can I make more memory on my &quot;/&quot;???"
date: 2008-01-26
forum: General Help
---

### Post by adn258 on 2008-01-26
Alright so I only made like 8 gigabytes of memory on my "/"   and the other like 200 is on my /home so like if there any way I could possible like move some memory from /home to "/"  I only have 4 gigs left on "/"

---

### Post by dcstar on 2008-01-26
> **adn258 said:**
> Alright so I only made like 8 gigabytes of memory on my "/"   and the other like 200 is on my /home so like if there any way I could possible like move some memory from /home to "/"  I only have 4 gigs left on "/"

That is not "memory", that is disk space.

If you want to resize partitions, do a search with those terms and you will find many posts with instructions.

---

### Post by jfinkels on 2008-01-26
Backup your data, boot from the Live CD, open Gparted, and resize the partitions to your fancy.

---

### Post by yabbadabbadont on 2008-01-26
This may help:  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Edit: Actually, the maintainer of that project is stopping.  The current version is only a month or so old, so it should still work.  However, he suggests using the following instead:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by adn258 on 2008-01-27
> **jfinkels said:**
> Backup your data, boot from the Live CD, open Gparted, and resize the partitions to your fancy.

Okay so like I did that and the partition screen comes up but like how do I actually do it?  I mean I know that sounds odd but when I press the little arrows up for memory it always make the memory less so like After I shrink one volume can I add it too another?  The memory shrunk?

---

### Post by wolfen69 on 2008-01-27
here [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) is a gparted tutorial.

---

### Post by jfinkels on 2008-01-27
> **adn258 said:**
> Okay so like I did that and the partition screen comes up but like how do I actually do it?  I mean I know that sounds odd but when I press the little arrows up for memory it always make the memory less so like After I shrink one volume can I add it too another?  The memory shrunk?

Select a partition, and choose to resize it. Shrink it to whatever size you want. Then resize the other partition and increase its size by extending it into the newly freed space (that you just freed by shrinking the adjacent partition).

---

