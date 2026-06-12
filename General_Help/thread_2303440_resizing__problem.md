---
title: "resizing / problem"
date: 2015-11-18
forum: General Help
---

### Post by cmcanulty on 2015-11-18
I need to add to my / partition but all the tutorials I see say it has to have empty space next to it. I have plenty of empty space on /home but it is at end not beginning of /home see screenshot. I would like to add 10GB to / and make /home 10GB smaller. I also have to be able to do this remotely

[ATTACH=CONFIG]265668[/ATTACH]

---

### Post by grahammechanical on 2015-11-18
It should be possible to resize sda2 from the left or the right. when you select the partition and choose to resize a arrow should appear at either end of the rectangle that is sda2. You can grab either one of those rectangles and slide them to resize. Or, you change change the size in the dialog box that appears. It will let you shrink sda2 to create space either in front or behind.

See this wiki page

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

See the second Image and the little box labelled New size (MiB). You can change the value by clicking an arrow so that there is free space preceding. Or following if that is what anyone wants.

Then when you resize sda1. You adjust the value of New size (MiB) upwards then you will see the values change in the box labelling Free space following (MiB).

Regards.

---

### Post by cmcanulty on 2015-11-19
no I only get the arrow on the right side of sda2 where I need space is left side, see screenshot. Will this have to be done from live cd or can I do it directly?

[ATTACH=CONFIG]265679[/ATTACH]

---

### Post by yancek on 2015-11-19
When you say you only see the arrow on the right side, are you referring to the black traingle?  If you move your mouse to the approximate location of that right arrow to the left side of the horizontal box, you should see a small white arrow.  Use that to move to the right.  You will be moving not only the partition but all the data inside which is at the beginning of the partition so you should have a backup of that data.   You could also use the boxes, lower the new size by 10GB and increase free space preceding by 10GB.  After doing this, you will be able to increase the size of /.

I generally use a CD/DVD/flash drive to modify partitions.  Since /home is on a separate partition, I would think you could make the change from the installed system but you can't make the change of resizing / from the mounted filesystem so better to use some other medium.

---

### Post by cmcanulty on 2015-11-19
I tried moving mouse all around and never see the white arrow. Also I have to do this remotely which may be impossible

---

