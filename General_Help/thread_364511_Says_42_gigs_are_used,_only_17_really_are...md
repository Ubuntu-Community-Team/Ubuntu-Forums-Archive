---
title: "Says 42 gigs are used, only 17 really are..?"
date: 2007-02-18
forum: General Help
---

### Post by Rippy on 2007-02-18
Ok, if I highlight everything in /, so essentially every file and folder in my system, it totals 17.6 gigs of data. That makes good sense, since I have 7 gigs of music plus UT2004 and some other things.

However, If I open up Disk Usage Analyzer, it tells me that 42gb of data is used, and that my 80 gig drive is 58% full. This is not true.

In nautilus, if I look at the properties of Filesystem, it conveniently tells me that I only have 26 gigs of free space left.

I also tried Mondo Rescue yesterday, but was appalled at how "Average" compression gave me 12gb of .iso files. Now it makes sense, because it was probably backing up 40 gigs of data.

First of all, what exactly is wrong? This is and old drive I got from my dad 3 or 4 days ago, so it's a fresh install. Is something odd going on that makes some of the empty blocks look full of data?

Second, how can I fix it? I would really like the back up my PC, and get an accurate reading of how much space is left.

Thanks!

-Rippy

---

### Post by solar george on 2007-02-18
> Ok, if I highlight everything in /, so essentially every file and folder in my system, it totals 17.6 gigs of data

Have you included hidden files and folders?

---

### Post by mcduck on 2007-02-18
One place worth looking at is /root/.Trash ;) Note that normal users don't have read rights to every place in file system, so you won't be able to get file sizes for those. Run 'gksudo nautilus' to take a better look inside /root for example.

---

### Post by Rippy on 2007-02-18
Yes, I did do a ctrl+h to show hidden folders before the ctrl+a.

Regardless, I don't have 42gb of stuff installed. This is a fresh install. My home folder is 8.5gb, the ut2004 folder is 5.4gb, and tremulous is perhaps 500mb, so that's about 14.5gb. Unless ubuntu somehow takes up 28gb for system files, 17 gigs should be about right.

Edit: Also, I realize that the swap takes up 5% of the drive's space. However, that would only be 4gb on my machine, not the 28gb that's mysteriously being used

---

### Post by Rippy on 2007-02-18
sorry, trying a bump because this fell off the first couple pages and I'd really like to be able to back up my PC today, which first requires that this problem be solved..

---

### Post by solar george on 2007-02-18
Try booting into recovery mode and doing an fsck

```
fsck.*filesytemtype* /dev/hda?
```

Replace the ? with your partition number.

---

### Post by Rippy on 2007-02-18
```
WARNING: performing this task on a mounted drive may cause SEVERE filesystem damage.

Continue? (y/n)
```
Either I'm doing something wrong, or fsck is not going to help me o_O

Edit: also, even when running nautilus as root, it's still 17.4gb.

---

### Post by solar george on 2007-02-18
OK

> ```
WARNING: performing this task on a mounted drive may cause SEVERE filesystem damage. Continue? (y/n)
```

Entirely correct. You may need to reboot using the live cd to do an fsck of your drive.

---

### Post by Rippy on 2007-02-18
Ok, did it with my live CD, here's the result:

```
/dev/hda1: clean, 153766/9633792 files, 11275930/19251886 blocks
```

Thanks for the help so far.. this thing still has me stumped :/

---

### Post by Rippy on 2007-02-20
bump?

---

### Post by Rui Pais on 2007-02-22
> **Rippy said:**
> Yes, I did do a ctrl+h to show hidden folders before the ctrl+a.

Regardless, I don't have 42gb of stuff installed. This is a fresh install. My home folder is 8.5gb, the ut2004 folder is 5.4gb, and tremulous is perhaps 500mb, so that's about 14.5gb. Unless ubuntu somehow takes up 28gb for system files, 17 gigs should be about right.

Edit: Also, I realize that the swap takes up 5% of the drive's space. However, that would only be 4gb on my machine, not the 28gb that's mysteriously being used

hi,
how do your swap is counted as drive used space? do you not set a partition for it?

Btw, did df report the same thing? Mind to post the output of: 
df -h

You could also use an utility like gdmap (gtk) or filelight (qt) that allow to easily see where the space has gone and which files are the bigger space eater.

Sometimes wrong size came from incorrect formats that set the size of filesystems smaller then partition sizes. 
You can check/solve the issue by running sudo resize2fs /dev/hda1 from a liveCD (on the unmounted partition).

hth

---

### Post by anaconda on 2007-02-22
ubuntu liveCD installer is a bit stupid, because it reserves 5% of disk space for root user in case if disk gets full.. so that root has enough free space to move around and make more space..

5% used to be good when disk sizes were ~1-2GB. Now with 300GB hd:s 5% is simply idiotic...

anyway my point was that you can adjust the reserved prosentage (And get more free space) either by installing with the alternate CD or running tune2fs after the installation.

eg.
tune2fs -m 0 /dev/hda1
would set the % to 0 which is good for every other partition than "/" for the root partition use:
tune2fs -m 1 /dev/hda1
to reserve only 1% for root..

Note: with both commands change the "hda1" to point to the partition you want..

---

### Post by trace_on on 2007-02-27
I'm having the same problem and it's driving me insane.
df says that / is 100% full, a total of 10GB used, while with du I see it's only really 1.8GB...
And I do see every file and I access every location in the search.
Any leads?

---

### Post by Rippy on 2007-03-04
Well, I've found my solution. It came from my ignorance of how the linux filesystem works :P

Turns out, my secondary 120gb fat32 drive was connected. I had never had to use it before in Ubuntu, so I forgot it was there. However, it was automatically mounted to /media, and was like 80% full.

I unmounted it, and baobab displayed the proper amount of space.

This still brings up an issue with Baobab though: you should be able to select only your primary hard drive, by having it exclude everything found in /media. Or maybe you can already do that and I just don't know about it >_>

Anyway, I figured I'd post this in case there are any others are as foolish as I was :P

---

