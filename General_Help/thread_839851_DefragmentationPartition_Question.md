---
title: "Defragmentation/Partition Question"
date: 2008-06-24
forum: General Help
---

### Post by IamReck on 2008-06-24
Alrighty...

So in Windows, I can defragment my HDD, and it moves everything over to the 'left' side of the bar.

In Ubuntu, I want to expand my / partition, currently on the right side of everything when you look at it in Gparted, but I want to be sure that it is not going to mess up any data that is on my /home partition, which is to the left of the / partition.  I also want to expand /home to the left, which will be going into my Windows partition.  Is there anyway to guarantee that I am not going to lose data when doing this?  A program or something that will look at where the data on my hard drive physially is?

Image of the situation, Windows on the Left, /home in the Center, and / on the right.

[[IMG]http://img50.imageshack.us/img50/9118/screenshotlu2.png[/IMG]]("http://imageshack.us")
[[IMG]http://img50.imageshack.us/img50/9118/screenshotlu2.794b7b9dae.jpg[/IMG]]("http://g.imageshack.us/g.php?h=50&i=screenshotlu2.png")

Thanks.

---

### Post by ibuclaw on 2008-06-24
If you use Vista, use Vista to shrink the size of your Windows partition. GParted cannot handle the resizing of NTFS partitions.

As for the other two, boot into the Ubuntu LiveCD and move/resize them accordingly.

No data will be lost in your Home and Root partitions. Gparted performs loads of checks pre and post moving of the filesystem.

Regards
Iain

---

### Post by IamReck on 2008-06-24
Awesome.  Thank you!

---

