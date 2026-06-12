---
title: "GParted LiveCD - Help resizing NTFS...!!"
date: 2007-08-16
forum: General Help
---

### Post by geek2330 on 2007-08-16
I used GParted LiveCD.

My drive is 120GB, originally partitioned as:

-20GB NTFS for WinXP Pro, this is my C drive.
-100GB NTFS for 2nd partition to store files, this is my D drive.

I am trying to upgrade my XP to Vista but Vista requires more than 20GB, so I decided to use GParted LiveCD to thrink my 100GB to 80GB, that worked ok.
No I have an "unallocated" 20GB partition between the C and D drives.

GParted doesn't allow me to increase the C partition and combine it with the other 20GB I just freed up.

This might be simple but either I missed something or this cannot be done.

Please help,

---

### Post by bruce2000 on 2007-08-16
Your spare unpartitioned space is located between C and D right?

Have you tried defragging your C drive and then trying to resize it?

---

### Post by geek2330 on 2007-08-16
I defragged C and D last night twice before I used Gparted.

Thanks for the quick feedback..!!

---

### Post by Arthur Archnix on 2007-08-16
Since you're going to put vista on it anyway, I'd just delete "C" and create a new partition in the free space. Unfortunately, I can't understand why you're not able to resize. Perhaps there is something on the gparted forums?

---

### Post by geek2330 on 2007-08-16
can't understand either, it allows me to thrink the C partition but not to increase it and take the unallocated space.

I am trying to upgrade instead of installing Vista from scratch....

.

---

### Post by Arthur Archnix on 2007-08-16
I see. Ok, well, how about we try the non-live version. Boot into ubuntu, go to a terminal and type:
```
sudo apt-get install gparted
```
Then you'll find gparted in your menu. Try to resize from there. If you run into problems, take a screenshot of gparted running under ubuntu and post it back here.

---

### Post by bruce2000 on 2007-08-16
As you're working with windows partitions you may have more luck using a windows partition manager such as Partition Magic

---

### Post by merlinus on 2007-08-16
Are both your partitions primary ones?

-merlin

---

### Post by geek2330 on 2007-08-16
> **Arthur Archnix said:**
> I see. Ok, well, how about we try the non-live version. Boot into ubuntu, go to a terminal and type:
```
sudo apt-get install gparted
```
Then you'll find gparted in your menu. Try to resize from there. If you run into problems, take a screenshot of gparted running under ubuntu and post it back here.

Here's the screenshot:

The first partition is the one I'm trying to increase, not sure why the yellow exclamation point.
The 3rd row is the unallocated available partition I'm trying to "append" to the first.

.

---

### Post by drpaul on 2007-08-16
That screen shows the problem [I think]. The unallocated space is in the extended partition and your C: partition is a primary partition. The program deoesn't know how to deal with that. I doubt that any parttion editing programs will.

HTH

Paul

---

### Post by Arthur Archnix on 2007-08-16
Yup. Extended partition. Looks like you have to delete /sdb5, then resize sdb2. it's an extended partition, which is like a container. Since sdb1 is outside that container, you can't extend it to take up the space that's free inside it. You have to delete the partition inside the container /sdb5 and then shrink the container /sdb2 so that there is room outside of it to expand the ntfs partition, sdb1.

This looks tricky, and is more than I've ever done before. Back up your data before attempting.

---

### Post by geek2330 on 2007-08-16
> **Arthur Archnix said:**
> Yup. Extended partition. Looks like you have to delete /sdb5, then resize sdb2. it's an extended partition, which is like a container. Since sdb1 is outside that container, you can't extend it to take up the space that's free inside it. You have to delete the partition inside the container /sdb5 and then shrink the container /sdb2 so that there is room outside of it to expand the ntfs partition, sdb1.

This looks tricky, and is more than I've ever done before. Back up your data before attempting.

Well, sdb5 is the free space I got by shrinking sdb6.
Sdb6 was originally about 90GB, this is the D drive. Then I used Gparted and shrinked it down to about 60GB.
This gave me an unallocated space that you see as sdb5, this free space is what I'm trying to "join" to my C drive which is the first row shown.

Am I out of luck?

.

---

### Post by merlinus on 2007-08-16
As Arthur said, you cannot add space from a logical partition to a primary one.

-merlin

---

### Post by geek2330 on 2007-08-16
Oh well,

Thanks guys,

---

### Post by Arthur Archnix on 2007-08-16
From what I've read, it's possible to resize an extended partition up, so I would *guess* that's it's possible to resize down. In your picture you posted, try this: If some step doesn't work you may as well just stop following my directions, I can't guarantee this will work.

Click inside the black disk. /dev/sdb5   Delete it. Right-click delete partition. It has to say "unallocated" not unkown". Once you have one space unknown, and one space green, all inside a light turquoze rectangle, you should click on the light-turquoize rectangle that surrounds the unallocated space, and the 62 gig /dev/sdb6. Resize that down, to just a little bit bigger than dev sdb6, or the same size if possible. 

You can also try clicking on /dev/sdb2 within the list below the graphical structure and try resizing it that way.

IF that works, you should be able to resize your ntfs parition (/dev/sdb1) up. 

IF not, sorry. Best of luck.

---

