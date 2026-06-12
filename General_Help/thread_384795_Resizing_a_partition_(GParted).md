---
title: "Resizing a partition (GParted)"
date: 2007-03-14
forum: General Help
---

### Post by Harold P on 2007-03-14
Hey everyone,

I'm having a problem with resizing a partition. (This is in GParted on a live CD)

Currently there is 30 GB of unallocated space, and I want to increase the size of one of my existing partitions to use that 30 GB. 

But, that's where the problem comes in. I can't. 

Here are some screenshots that may better help describe my problem:

[IMG]http://img471.imageshack.us/img471/1698/screenshotgpartedtj5.png[/IMG]
(Shows the 30 GB being unallocated)

[IMG]http://img482.imageshack.us/img482/5233/screenshotresizedevsda4ey3.png[/IMG]
(The dialogue that asks me how I want to resize the partition I want to increase. It will only make it smaller, and not use the free 30 GB.)

If you need anymore information I'll post it.

And no, none of those partitions are mounted but the partition I want to resize is in my /etc/fstab

Anyone have any ideas? Maybe I overlooked something?

Thanks for the help!

---

### Post by kolinab on 2007-03-14
From my understanding of how this works, in your particular situation you can expand sda1 into that space if you like. You MAY even be able to expand the beginning of sda2, but I think I read somewhere can you can only expand the end of partitions, not the beginning. 

It's not letting you expand sda4, because I believe it requires the partition to be an actual contiguous block of space on the drive. Straddling sda2 doesn't work.

---

### Post by Harold P on 2007-03-14
Well. I thought that adding the 30 to sda2 would work, and then putting the 30 at the end of sda2 would work, but it doesn't.

Have any idea? I'm going to try the newer version of the LiveCD out. I'm using GParted .1 right now, so my method of adding the space may just be unsupported.

Thanks for the help, though. :)

---

### Post by Kateikyoushi on 2007-03-14
I would try the latest gparted live cd that has the best chance of succeeding. [LINK]("http://gparted.sourceforge.net/livecd.php")
As already said you can not resize a partition which is not even close to the free space.
Can't you put the data on other partitions ? Then could delete and create new partitions the size you want.

---

### Post by jjross on 2007-03-14
From the looks of your screenshot  the partition you are trying to increase the size of is inside an extended partition that is still mounted.
You need to unmount the extended partition and expand it so that you can expand the one inside of it.
Edit: My mistake,  I thought you were trying to move sda1
if you are trying to expand sda4 into that space you will need to make room after it to expand it in to.
A very interesting problem you have there, you some how need to get the free space after sda4.

Edit #2 maybe you can create a new partition in the free space and copy sda4 into it with Partimage. [http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by Harold P on 2007-03-15
The first image disappeared, so here it is again (this is on my regular linux partition, not the ubuntu live CD; yes everything is mounted except the unallocated space):

[IMG]http://img354.imageshack.us/img354/4702/screenshotdevsdagpartedxo8.png[/IMG]

Okay, so if I was to copy the partition into the 30 GB unallocated space, what would I do with the 20 GB remaining? (the original partition?). And if I was to move sda2 to the remaining 20 GB, would that affect anything since *is it the boot partition*? And GParted also is telling me about not being able to create more than 4 partitions. 

[IMG]http://img259.imageshack.us/img259/6996/screenshotgpartedqd2.png[/IMG]

---

