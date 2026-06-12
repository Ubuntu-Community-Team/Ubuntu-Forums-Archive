---
title: "partitioning question"
date: 2008-06-08
forum: General Help
---

### Post by ZAX2717 on 2008-06-08
hello im a new linux user and im loving every minute of it! now i have my laptop hard drive set up with 3 partitions: linux Ext3 partition, the swap partition and unallocated space where i was going to put windows. but now ive changed my mind and i would like to just run windows since i found out how to run the two programs i wanted in linux (half-life 2 and photoshop) no i was wondering if theres any kinda program that could add the unallocated space to the ext3 partition? this would make things a lot easier for me and thanks for the input.

Zach

---

### Post by MDSmith2 on 2008-06-08
First, download the [gparted]("http://gparted.sourceforge.net/") livecd.
Then once in the partitioner, right click the swap partition and click "resize/move" and in the "free space following" field following type 0 and confirm the move and once that is done, Right click the ext3 partition and click resize/move and in the "new size" field hold the up button till it stops and confirm it.
this may take awhile if you have a big partition.

---

### Post by drs305 on 2008-06-08
> **ZAX2717 said:**
> but now ive changed my mind and i would like to just run windows since i found out how to run the two programs i wanted in linux (half-life 2 and photoshop) no i was wondering if theres any kinda program that could add the unallocated space to the ext3 partition? this would make things a lot easier for me and thanks for the input.

Zach

I think you meant you wanted to "just run **linux**"?

If that is the case, there is a program called **gparted** that can expand your partition. 

1. Make a copy of any valuable data you have already put on the drive - the linux partition to be exact.

2. Boot with the LiveCD and then open gparted. You need to do this with your linux partition unmounted, which is why you boot from the liveCD. It will allow you to resize the linux partition. You should be able to do this without data loss but copy your personal data anyway. 

Even better, make the extra partition and keep your data on that one. You can even move your /home over to the new partition, which many people recommend.

Here is a link on how to make a separate /home partition - but do this later.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Rocket2DMn on 2008-06-08
I assmume you mean you want to run linux only.  You can use your LiveCD to resize the partitions.  Boot into the LiveCD and go to System->Administration->Partition Editor.  From here you can resize your ext3 partition into the empty space, though you may need to move your swap space to the end of the drive first, depending on the configuration.

You can do the same thing using the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by ZAX2717 on 2008-06-08
hey thanks alot everybody im gonna try this out but im pretty sure it will work i had a feeling ubuntu had a program somewhere that did this i just wasnt sure but thanks again!

EDIT: yeah it worked thanks for the help guys

---

### Post by MDSmith2 on 2008-06-09
No problem!

---

### Post by VMC on 2008-06-09
> **ZAX2717 said:**
> hey thanks alot everybody im gonna try this out but im pretty sure it will work i had a feeling ubuntu had a program somewhere that did this i just wasnt sure but thanks again!

EDIT: yeah it worked thanks for the help guys Since you havn't label this solved yet, I would like to add my thoughts.

I have used Windows for way to many years, and I came to depend on Acronis Disk Director. Even when I moved to Linux I still used that program.

Now that I have come to realize the power AND stability of Gparted, there's no going back! If yo have time and a spare hard drive play around and get comfortable with Gparted. It will pay you dividends in the future.

---

### Post by MDSmith2 on 2008-06-09
> **VMC said:**
> Since you havn't label this solved yet, I would like to add my thoughts.

I have used Windows for way to many years, and I came to depend on Acronis Disk Director. Even when I moved to Linux I still used that program.

Now that I have come to realize the power AND stability of Gparted, there's no going back! If yo have time and a spare hard drive play around and get comfortable with Gparted. It will pay you dividends in the future.
Your right.
It always good to be comfortable with your partitioner.

---

