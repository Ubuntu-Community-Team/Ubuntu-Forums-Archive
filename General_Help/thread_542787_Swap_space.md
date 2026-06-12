---
title: "Swap space"
date: 2007-09-04
forum: General Help
---

### Post by jsvidyad on 2007-09-04
Hi!!


    I came across an article saying that in linux, the maximum size for a swap partition is 2 GB. Right now, I have put up a 4GB partition as swap. Do, I have to break it up into two 2GB swap partitions??

---

### Post by rsambuca on 2007-09-04
How much ram do you have?

---

### Post by ddrichardson on 2007-09-04
Aside from why you'd want so much...

The answer is yes and no. 2Gb is the swap space limit, per partition - but 2.4.10 kernels support up to 32 swap devices.

---

### Post by fragos on 2007-09-04
The normal recommended size that of your real memory.  The size recommended when partitioning may be larger.  I increased my memory size until the free command showed that swap space wasn't used.  This occurs on my system at 1GB.

---

### Post by jsvidyad on 2007-09-26
I have 2 GB RAM. That's why I set up a 4 GB swap partition. Do I have to split it into two 2 GB swap partitions?? Does ubuntu allow multiple swap partitions??

---

### Post by dabl on 2007-09-26
> **jsvidyad said:**
> I have 2 GB RAM. That's why I set up a 4 GB swap partition. Do I have to split it into two 2 GB swap partitions?? Does ubuntu allow multiple swap partitions??

I strongly recommend you set your swap partition at 0.5GB, and don't plan on seeing any of that used.  More than that will be wasted space -- I've been watching mine for a year, and running multiple instances of audio file encoding it's never been over 30MB of swap usage.  :)

---

### Post by shishirmk on 2007-09-26
ideally swap should be 1.5 times your ram size....

---

### Post by rsambuca on 2007-09-26
> **shishirmk said:**
> ideally swap should be 1.5 times your ram size....

Not true at all.  Your swap size will depend on your usage and needs.  If you wish to use the 'hibernate' feature, then it must be bigger than RAM.  If you are not going to use 'hibernate', then you probably don't need any swap with 2GB RAM.

---

### Post by LaRoza on 2007-09-26
> **shishirmk said:**
> ideally swap should be 1.5 times your ram size....

Someone on the forum had a computer with 8 gigs of RAM. In that case, large swap, or any swap was useless for the use of the computer.

For most setups, 256 - 512 MB of Swap works fine.

---

### Post by dabl on 2007-09-26
> **rsambuca said:**
> 

 If you wish to use the 'hibernate' feature, then it must be bigger than RAM. 

 

That's true -- that's the one case that requires swap size 1.5x RAM, except for ancient machines with small RAM -- sorry, I'm too desktop-centric!  :)

---

### Post by jsvidyad on 2007-11-02
Hi!!


    My question was can ubuntu use the present 4 GB swap space or do I have to break it into two 2 GB swap spaces??

---

### Post by louieb on 2007-11-02
> **jsvidyad said:**
> ... or do I have to break it into two 2 GB swap spaces??
What does the command** top **show?
If in show you have 4GB swap then your fine.
IF not Ubuntu will use multiple swap partitions even if they are on separate drives.

---

### Post by fragos on 2007-11-02
Swap space has always been a shared thing between multiple boots of Linux.  For some reason when I installed 7.10 to dual boot with 7.04 I ended up with two swap spaces.  The added one is smaller than the other so size shouldn't have been a reson for this happening.

---

### Post by dcstar on 2007-11-02
> **jsvidyad said:**
> Hi!!


    My question was can ubuntu use the present 4 GB swap space or do I have to break it into two 2 GB swap spaces??

It will use whatever swap space it has been given to use.

The command **swapon -s** will show you what is in use.

Chances are if you have over 1GB of RAM and don't do video editing (or any other RAM hungry process), then your system will never use any of the swap space you have set up.

---

### Post by minus198 on 2007-11-02
Is there any way of removing some of the Swapspace an expanding the mainpartition?

---

### Post by dcstar on 2007-11-03
> **minus198 said:**
> Is there any way of removing some of the Swapspace an expanding the mainpartition?

Use the swapoff command to disable swap, delete the partition, recreate it as small as you need placing it so you have space to expand your other partition, then use swapon to enable it.

Expanding your other partition depends on if you can unmount it in normal operation, or use the Live CD to do it.

---

### Post by ntu on 2007-11-04
> **dabl said:**
> I strongly recommend you set your swap partition at 0.5GB, and don't plan on seeing any of that used.  More than that will be wasted space -- I've been watching mine for a year, and running multiple instances of audio file encoding it's never been over 30MB of swap usage.  :)

How can you see the maximum amount of swap that has been used by your computer?

---

### Post by rsambuca on 2007-11-04
You can open a terminal "Applications -> Accessories -> Terminal" and enter the simple command:```
free
```

---

