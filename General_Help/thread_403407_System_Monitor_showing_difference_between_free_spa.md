---
title: "System Monitor showing difference between free space and available space"
date: 2007-04-07
forum: General Help
---

### Post by llamapalooza489 on 2007-04-07
Yesterday I looked at my space available/space used, and it showed something about 2.3 gigs, which seemed right. Then today when I opened up my Home folder, it showed only 1.6 gigs available.  I opened up System Monitor and checked my Free and Available space.  Free is showing 2.2 gigs, and available is showing 1.6 gigs.  What happened to the other 600 mb?  by the way, i'm running edgy.  I've attached an image showing the file system info

---

### Post by llamapalooza489 on 2007-04-07
anybody have an ideas?

---

### Post by lordViN on 2007-10-31
I'm having the same problem but with all my ext3 partitions, Gparted also shows that I have the space marked as free in the system monitor as unused space, that is in total like 23GB that I cannot use and I need. 

any clues?? what the problem could be? is a problem with the ext3 file system?

---

### Post by forestpixie on 2007-10-31
it might be due to the fact that about 5% of drive space is reserved for root - obviously more importnat in / where you're program files etc live - I changed it on my data drives so that no disc space was reserved, but didn't change it in the / drive

I can't find on the forum or remeber how I did it - but it was using tune2fs - try searching for that

In the meantime if I remember I'll post

---

### Post by nowshining on 2007-10-31
it could also be logs or tmp files :)

---

### Post by lordViN on 2007-11-01
I was able to find a solution to the reduce the reserved space.

is here: [http://ubuntuforums.org/showthread.php?t=561202&highlight=reserved+space+ext3](http://ubuntuforums.org/showthread.php?t=561202&highlight=reserved+space+ext3)

And I have one more question, It is safe to use the "tune2fs -m 0 "device" on a /home directory? does the /home directory use privileged root processes? 

thanks to all for your help,

---

### Post by anaconda on 2007-11-01
> **lordViN said:**
> And I have one more question, It is safe to use the "tune2fs -m 0 "device" on a /home directory? does the /home directory use privileged root processes? 

The only reason 5% is reserved for root is that if the disk gets full, then you can boot to recovery mode as root and you have enough room to move around and make more room.

But you can do that just as well with a liveCD, so that isn't THAT necessary. And even then 100MB would be more than enough space for that purpose.

I have always set the procentage to be 1% on the "/" partition and 0% on every other partition.

And by the way. 5% is ridiculously much. It used to be good procentage when harddisk sizes were about 500MB. I thing the default value should be made smaller.

---

### Post by nowshining on 2007-11-01
> **lordViN said:**
> I was able to find a solution to the reduce the reserved space.

is here: [http://ubuntuforums.org/showthread.php?t=561202&highlight=reserved+space+ext3](http://ubuntuforums.org/showthread.php?t=561202&highlight=reserved+space+ext3)

And I have one more question, It is safe to use the "tune2fs -m 0 "device" on a /home directory? does the /home directory use privileged root processes? 

thanks to all for your help,

thanks for that url i'll give it a shot.. :)

---

