---
title: "Resizing root partition?"
date: 2007-03-09
forum: General Help
---

### Post by georglind on 2007-03-09
Hi,

I'm pretty new with linux, and is running kubuntu for like one month. 

I tried installing maple, but it didn't work due to lack of space. My computer is fairly new,  and there's plenty of space left so I guess somethings wrong with the way I partitioned the harddisk. 
I've attached a screenshot of the partition shown by qtparted, where as you can see the root-partition (dev/sda1) is almost filled. 
But what I would like to know is whether it has anything to do with the partition-thing, and how I can fix it... I can't resize the partition using qtparted. Is this because the partitions are mounted, and how do I unmount them and make a resize? 
I would really appreciate some good advice..

Thanks in advance
Kim

---

### Post by jem7v on 2007-03-09
Personally, I would recommend downloading the gparted LiveCD and doing it that way.  Basically, if you booted off your hard drive, it has to be mounted, so the only way to edit the partitions is to boot from a LiveCD (afaik).  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) talks about resizing/creating partitions, and you can find the gparted LiveCD **[here]("http://gparted.sourceforge.net/livecd.php")**.

---

### Post by georglind on 2007-03-10
Thanks, that worked really nice. The gparted live cd was really intuitive, and thus made the repartioning easy to handle.

---

### Post by ubu-for on 2007-03-14
> **georglind said:**
> The gparted live cd was really intuitive, and thus made the repartioning easy to handle.

I don't get it.

My root partiton has nearly no space left, too. I've tried to resize it with the GParted LiveCD but I can only shrink my partitions.

So I've shrinked the /dev/sda2 partition but don't know how to add the free 5.4 GB of the new /dev/sda4 partition to the root partition.

THX for your HELP!

---

### Post by georglind on 2007-03-14
I don't know that much about ubuntu or linux so if what i'm writing is nonsense. Just overlook it.. :)

That you can't grow any partitions might be because there is no place growing them. If this is the case you should be able to grow your home partition back to the normal size (but you don't wanna do that).

As far as I know the partitions are stacked on top of each other. It shows so in the Gparted partition bar, where your root partition is placed most left, then the other partitions placed afterwards with the home directory followed by some of your freed space at the right.
Or so I guess since you haven't included the bar on your attachment.

Now you have to move that free space all the way down to the root partition. this can be don by moving every one of your partitions to the right starting with the home partition. It took like 12 hours for me to move /home, but I don't know wether there is a smarter way...

Hope this was of any help...

---

### Post by ubu-for on 2007-03-17
> **georglind said:**
> I don't know that much about ubuntu or linux so if what i'm writing is nonsense. Just overlook it.. :)

That you can't grow any partitions might be because there is no place growing them. If this is the case you should be able to grow your home partition back to the normal size (but you don't wanna do that).

As far as I know the partitions are stacked on top of each other. It shows so in the Gparted partition bar, where your root partition is placed most left, then the other partitions placed afterwards with the home directory followed by some of your freed space at the right.
Or so I guess since you haven't included the bar on your attachment.

Now you have to move that free space all the way down to the root partition. this can be don by moving every one of your partitions to the right starting with the home partition. It took like 12 hours for me to move /home, but I don't know wether there is a smarter way...

Hope this was of any help...

THX!

---

