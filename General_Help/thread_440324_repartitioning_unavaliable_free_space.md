---
title: "repartitioning unavaliable free space"
date: 2007-05-11
forum: General Help
---

### Post by kduffy6 on 2007-05-11
When I installed Ubuntu, i partitioned my 80gb hard drive so i have 60gb for windows because i was still unsure if i was going to really use linux instead. When it was fully installed, it wiped my hard drive including the windows os. I decided to go with it and just use linux and it has turned out nicely, except that i went to add all my music from my external and got an error saying not enough space. i realize dit was because i had only 10gb partitioned to my /home directory. how do i change this?? i typed in sudo gparted and this brought up the list of partitions, but i dont know how to change any of them. there is one listed as unallocated and has 60gb of space. i want to add this to my /home directory, but i am unsure as to how to do this...any help would be great. thanks!

---

### Post by carlosqueso on 2007-05-11
First, you'll need to use a live CD to do this, as trying to mess with mounted partitions is ugly and gparted won't let you do it.  If you don't have an ubuntu CD handy, try the gparted live cd at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

Then you have two choices.  If your /home partition is next to (physically) the free space, you should be able to just resize it to fill the space.  otherwise, I'd reccommend just creating a new partition on the free space, marking it as /data or some such, and setting permissions so that you can access it.  Then, if you want it to be really easy, create a link to it in your /home directory.  If you need help with the latter steps, just post and somebody can help you.

---

### Post by kduffy6 on 2007-05-11
does anyone know how to do any of this? this is still my first week of linux so theres a lot of simple things i dont know how to do yet. thanks

---

### Post by carlosqueso on 2007-05-11
Before you do anything else BACK UP ALL YOUR DATA ON /HOME!!!!


Okay, first download and burn that cd in the link I gave you.  Then, put it in the drive and restart the computer.  Gparted should come up automatically after it boots.  Then you'll have to look at the partition.  If the partition you are using for /home is next to the unpartitioned space, click it, click "resize" and make it as big as possible.

If it's not, you'll have to create a new partition by clicking the unpartitioned space and clicking "new".  If you have to do that, post back and I'll walk you through setting up your fstab.

---

### Post by kduffy6 on 2007-05-13
thanx for the help. i had stuff to do this weekend, so thats why it took me forever to get around to doing this, but it worked. thanx so much!

---

