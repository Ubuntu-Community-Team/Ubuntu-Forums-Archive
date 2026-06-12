---
title: "[SOLVED] Gparted error working with large drive"
date: 2008-07-09
forum: General Help
---

### Post by djbon2112 on 2008-07-09
I have a RAID5 array of 4x 750GB HDDs on my storage server (running Ubuntu Server 8.04 x64) for a total size of 2.05 TiB according to Gparted. However, if I try to create a partition (any filesystem) of that size it automatically resizes to exactly 46.38 GiB and I can't resize it. If I try any size less than the max, it doesn't auto-resize, but I get the error "a partition cannot have a length of -1 sectors". This happens until I get to about 1.12 TiB at which point the partition will be created fine, but if I try to resize THAT I get the same error only substituting the -1 for a large negative number.

Is there any way around this? I need this entire array to be one filesystem so simply breaking it up isn't an option. I need to get this working ASAP so any help would be appreciated!

---

### Post by djbon2112 on 2008-07-09
Update: Same issue with plain ol' parted, so it seems to be an issue with that and not gparted in particular. Are there any other partitioning options open to me, or some sort of workaround for this issue?

Sorry if I sound persistent, but I really need an answer and Google is turning up a blank.

---

### Post by tagra123 on 2008-07-09
Not an answer -- just some info

Max Partition Sizes

[http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php](http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php)

You can combine partitions using LVM

[http://eatingsecurity.blogspot.com/2008/03/using-parted-and-lvm2-for-large.html](http://eatingsecurity.blogspot.com/2008/03/using-parted-and-lvm2-for-large.html)

Also, I wonder if RAID is part of the problem.

---

### Post by djbon2112 on 2008-07-09
It's a RAID on a Dell Perc 5/i, but I don't think that's the problem, since I can create smaller volumes on it just fine. Also I'm using XFS, but the problem is the same regardless of the filesystem (tried ext2, ext3, xfs, jfs, even the extended partition fails). Could it be a bug in parted perhaps? The negative numbers in the error suggest this isn't normal operation.

If it matters, the remaning free space after the "resize" is exactly 2 TiB. Here's a screenshot:

[[IMG]http://img20.imageshack.us/img20/8745/screenshottightvncadminpc8.th.png[/IMG]](http://img20.imageshack.us/my.php?image=screenshottightvncadminpc8.png)

And of me getting the error:

[[IMG]http://img74.imageshack.us/img74/3541/screenshottightvncadmingd5.th.png[/IMG]](http://img74.imageshack.us/my.php?image=screenshottightvncadmingd5.png)[[IMG]http://img210.imageshack.us/img210/5791/screenshottightvncadminlf2.th.png[/IMG]](http://img210.imageshack.us/my.php?image=screenshottightvncadminlf2.png)

---

### Post by cariboo on 2008-07-09
You may want to give fdisk a try.

```
man fdisk
```

Cfdisk would probably be better but I see it isn't in the repositories.

Jim

---

### Post by fjgaude on 2008-07-10
If memory serves, I used this link to get **cfdisk**:

[http://packages.debian.org/etch/cfdisk-udeb](http://packages.debian.org/etch/cfdisk-udeb)

cfdisk is what I use.

I also think that many Linux programs may not have updated to the huge disk drives that have come on the market in the last year or so. These -1 reports point to this... not enough integers in the math equations.

---

### Post by djbon2112 on 2008-07-10
Thanks guys, trying those now. I'll get back with the results!

EDIT: I can't seem to find cfdisk. I go to that page, but I get a dependancies not satisfied error, and all its dependancies can't be found. Are there any standalone Ubuntu .debs for cfdisk?

---

### Post by fjgaude on 2008-07-10
I don't know of any for Ubuntu... I didn't have any issues with dependencies... strange.

Try another google site to see if you can find cfdisk somewhere else.

---

### Post by djbon2112 on 2008-07-10
It's an issue with libslang2-udeb, which requires libc6-udeb, but I can't install that without an error ("Cannot overwrite libcrypt.so.1 which is part of libc6").

---

### Post by djbon2112 on 2008-07-11
I'm still having trouble trying to get cfdisk working, but I'm also trying to upgrade parted from the default 1.7.1 to a new version (1.8.6). Hopefully this will be of some help.

---

### Post by djbon2112 on 2008-07-12
Even the latest version of parted (1.8.8) has this same problem. I'm still open to trying to get cfdisk working, but the problem lies in that it dependso on packages that are -udeb, instead of the regular ones I have installed on my system. Any advice?

---

### Post by djbon2112 on 2008-07-12
There is something REALLY wrong here... even fdisk/cfdisk only create a 46GB partition! But I don't see how it's a problem with the controller since I can create many smaller paritions, but I can't see how 2 different versions each of 2 different Linux partitioning programs are having the same problem! 

This is frustrating to the max.

Here's cfdisk after doing the following:

Creating a partition of the max size, then ctrl+c
Creating a new partition of the max size in the 2 TiB of free space, then ctrl+c
Opening the program again

[[IMG]http://img401.imageshack.us/img401/4479/screenshottightvncadminpa5.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshottightvncadminpa5.png)

---

### Post by djbon2112 on 2008-07-13
I checked out the controller's settings and it can't be the culprit as everything is set correctly. This must be a problem with Linux. Can anyone offer any suggestions to get this bug fixed? (I don't want to use LVM and hack a couple partitions together in case I need to move the RAID to a new system/the OS crashes/etc.)

---

### Post by djbon2112 on 2008-07-14
Well, I got it. I folowed the first few steps of [http://eatingsecurity.blogspot.com/2008/03/using-parted-and-lvm2-for-large.html](http://eatingsecurity.blogspot.com/2008/03/using-parted-and-lvm2-for-large.html) to the letter, doing:

```
sudo su
parted
(parted) mklabel gpt
(parted) mkpartfs primary xfs 0 2249G
(parted) quit

```

...then formatting the partition to actual XFS using gparted. It must've been because I was using an msdos partition label instead of gpt, and I never knew to change that since I had no idea what any of the other ones than msdos (like gpt) were.

Marked solved. If you have this problem, use a gpt label instead of the default msdos!

---

