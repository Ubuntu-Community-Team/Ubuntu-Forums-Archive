---
title: "Help with dualbooting XP"
date: 2007-05-03
forum: General Help
---

### Post by nekodromeda on 2007-05-03
Hi, I'm a bit of a newbie and don't know what I'm doing, but I hope you can help.

I just recently tried installing 7.04 on my laptop and for some reason (over-partitioning? I don't know) I ended up not having enough memory to start Ubuntu. So I decide to try reinstalling it and to clear off as much space as possible by going into Manual for partitioning. So I delete all of the partitions except for one (I don't remember the name, but it was the biggest one under /dev/sda) and install.

My problem is now my computer boots straight into Ubuntu, with no stopping by Go, no collecting 200$, and certainly not letting me choose between Ubuntu and XP. This wouldn't be such an issue if I didn't have a fair bit of really important data still on XP. A friend suggested running something called FixMBR to try to find the partition, but the warning says that it could damage the partition tables and cause all the partitions to become inaccessible. Is this really what I should be doing? Does anyone know a way to fix this? I would like to be able to dualboot XP, but for now I'd be satisfied with just having the data. Thanks.

---

### Post by m.musashi on 2007-05-03
It's hard to know exactly what is going on without a bit more information. However, if you deleted all partitions except one then it is possible that you installed to the same partition that contained XP - which means that XP is now gone. However, that is just speculation right now based on what you have said. In order to get a bit more info, open a terminal and do
```
sudo fdisk -l
```
Just copy and paste. If you type it, the last part is a small letter L. That will show us what partitions exist on your drive(s).

---

