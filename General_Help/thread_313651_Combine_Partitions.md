---
title: "Combine Partitions"
date: 2006-12-06
forum: General Help
---

### Post by element on 2006-12-06
I had my system setup for dual boot.  I formatted the two NTFS partitions to ext3.  Now I want to combine the two partitions.  How do I do this?  Gparted wont do it for me.  I can resize, but cannot move one partition to another or combine.  I even tried the live cd thinking I couldnt be using the drive while I made those changes.  Still no luck. What am I doing wrong? How do I combine two partitions on one hard drive.  Ideally what I would like to do is add them to the main partition, but I dont know if this is possible.

I want to take sda1 and sda2 and add them to sda5.
See screenshot...
[IMG]http://i13.tinypic.com/2rdb7h2.gif[/IMG]

---

### Post by taurus on 2006-12-06
It could be because /dev/sda1 & /dev/sda2 are primary partitions while /dev/sda5 is logical parition!!!

---

### Post by element on 2006-12-06
When I first installed Ubuntu it automatically partitioned that way.  Now I am getting rid of XP and want those partitions back. I guess I dont understand the difference between logical and primary partitions and why it would matter to combine them or not to combine them.  Can you explain in more detail please. Thx.

---

### Post by taurus on 2006-12-06
You can only have four primary partitions on a harddrive!!!  If you need more than four, then you need to convert one of the primaries into extended partition and create many logical partitions under that extended partition.  As you can see from the screenshot, your /dev/sda1, /dev/sda2, & /dev/sda4 are primary partitions while /dev/sda3 is your extended partition.

---

### Post by element on 2006-12-06
Thanks for the info.  
So how do I convert one of the primaries into an extended partition ?  I deleted it and then when I try in gParted to create a new partition it forces me to select primary. Logical and extended are greyed out.  My guess its because there is already a logical partition created (/dev/sda3). Correct? Not sure how to get past this point.

---

### Post by taurus on 2006-12-06
Yes, you can only have on extended partition (and many logical partitions under it).  If you can backup your important files, I recommend you delete everything and start it from the beginning.  If you plan to have more than four partitions, make the last one as an extended partition and use it to create some logical partitions.  It's a good idea to use the last partition (doesn't have to be the fourth primary partition) as your extended partition.

---

