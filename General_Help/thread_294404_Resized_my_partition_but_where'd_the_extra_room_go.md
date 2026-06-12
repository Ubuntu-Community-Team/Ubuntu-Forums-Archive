---
title: "Resized my partition but where'd the extra room go?"
date: 2006-11-06
forum: General Help
---

### Post by FastZ on 2006-11-06
I logged into Windows and using Paragon Partition Manager, I resized my 10gb Linux partition to take over the empty, unformatted space before it (27gb approx.). The resize went smoothly without error, I booted into Ubuntu just fine after a disk check said that it found errors and fixed them. But now, my Desklet that monitors hard drive space still says that I only have 10gb of space on this partition. How do I find out if the 27gb I just added is actually usable? ](*,)

---

### Post by hexion on 2006-11-06
In linux partitions (at least ext3) it's not enoght to resize the partition. There's metainfo in the partition that maps the space.

I had to do the same some time ago, and there were 2 steps. First, phisically resizing the partition. And last, telling ext3 that its space is now bigger.

Sorry, I don't remember the commands nor the post.

---

### Post by subzero79 on 2006-11-06
Try using Gnome Partition Editor included in Ubuntu or the Disc manager. i believe is system->admin->Discs

---

### Post by FastZ on 2006-11-07
@hexion
It would be awesome if you could pick your brain a little and help me find out what you had to do. This is aggrevating me to no end that I have all this extra space but cant use it for anything.
 
@subzero79
Cant find that in Edgy...the system>admin>discs part anyway. The GParted thing I will have to look for and try out.
 
Thanks to both of you.

---

### Post by hikaricore on 2006-11-07
I searched the forums for this awhile back after I had a similar problem, I'll poke around today and try and find an answer for you, it was something really simple tho. :)

---

### Post by FastZ on 2006-11-07
Exactly, it seems like it would be simple 1-2-3 step process but finding how to do it is what's driving me nuts!  I have read about half of the threads on here that concern partitioning but I have yet to find one that actually gives an answer to the question that started the thread.  They all just get about halfway into the problem and then just cut off.

---

### Post by hikaricore on 2006-11-07
Ok, I looked and looked and looked and didn't find the information that I found once before, and I tried ever variation of "disk size wrong"-"partition size incorrect" across the board up down and sideways.  So I'm sorry to say I won't be of much help.  I'm pretty sure I remember it had to do with e2fsck.  You may want to boot from a live cd and try running e2fsck on your drive with the repair flag and force checking:

```
e2fsck -fp /dev/hd??
```

where ?? is your drive location

I know there was another step to this, some other tool I used that instantly solved the problems I was having.  But I just can't track it down.  :(  Anyway backup anything important before messing with a disk at all.  And hopefully someone will come along and give you the info you need.

---

### Post by FastZ on 2006-11-07
If you replied to that thread wouldn't it show up when you searched for all your posts?
 
When i get home, I'll run that e2fsck command and see what comes up.  The disk should be fine though.  Automatically ran a chkdsk on it during bootup after I resized the partition and two errors had shown up but were fixed.

---

### Post by hikaricore on 2006-11-07
> **FastZ said:**
> If you replied to that thread wouldn't it show up when you searched for all your posts?
 
When i get home, I'll run that e2fsck command and see what comes up.  The disk should be fine though.  Automatically ran a chkdsk on it during bootup after I resized the partition and two errors had shown up but were fixed.

I tried that too, evidently I never replied to that thread >.< or in any way marked it for myself *sigh*.  I was in a bit of a rush that day as the system in question was one of the servers I use in my office.  It needed to be back online and have disk space. lol

---

### Post by FastZ on 2006-11-07
Good call.  Oh well.

---

### Post by FastZ on 2006-11-07
Alright, I feel like a retard.  I was searching around hoping to come across something that you might have used back when you had this problem and found [this thread]("http://www.ubuntuforums.org/showthread.php?t=251799&highlight=disk+size+wrong") started by a guy who had pretty much found himself in the same predicament that I find myself in now.  They seemed to get an answer on there and the guy ended up fixing his problem so I will try that once I get home to see if it works for me the same as it did him.  Thanks for the help.

EDIT:  went in and resized the partition with the gParted LiveCD just teeny bit and then applied the changes and gParted extended the ext3 filesytem on the partiton to fill the entire partition so now I'm all good.  Thanks for the help.

---

### Post by hikaricore on 2006-11-08
Glad to hear you got it working :)  All I know is that my problem was with an ext2 partition but had a similar issue and I ended up using a command line process to fix the size.  Lol, you did much better in your case.  :)

Cheers

---

