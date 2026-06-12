---
title: "swap in Ubuntu 14.04"
date: 2014-03-14
forum: General Help
---

### Post by jackson21 on 2014-03-14
Hi, all
The "swap" partition  question has been answered a million times,
swap is 2.5 times the ram capacity ??!!
For the new Ubuntu 14.04 I will set up a new PC with 8GB ram chips
So it means that  I have to set up a 16 GB drive for swap.
Thank you all for help

jackson

---

### Post by 3rdalbum on 2014-03-14
> **jackson21 said:**
> Hi, all
The "swap" partition  question has been answered a million times,
swap is 2.5 times the ram capacity ??!!
For the new Ubuntu 14.04 I will set up a new PC with 8GB ram chips
So it means that  I have to set up a 16 GB drive for swap.
Thank you all for help

jackson

Swap is not compulsory. On an 8 GB machine, the only thing you'd want swap for is hibernation. If you don't hibernate the computer, or if you suspend the computer instead of hibernating it, you don't need any swap at all. Heck, 8 gigs of RAM is a ridiculously large amount for an ordinary desktop computer. I'd even say that I'm scandalized by the wastage, because probably half of your RAM will never be touched.

The 2.5x RAM capacity rule comes from years ago when computers came with 128 megabytes of RAM, and it's a *suggested maximum*, not a minimum. Any more than 2.5x RAM and you'll experience lower performance. Less doesn't hurt.

In short: If you hibernate, allow your RAM size plus 1 GB (for instance, if you persist with buying 8 gigs of RAM, have a 9 gig swap partition). If you don't hibernate, don't bother with swap. You can always change your mind later and add it if you start doing high-end scientific analysis.

---

### Post by buzzingrobot on 2014-03-14
Load a batch of large image files for processing in Gimp, say, and you can gobble up 8 gigs without breaking a sweat.

if you routinely have tasks that resort to swap, you'll know it because everything will be annoyingly slow. At that point, forget about advice about how big to make the swap partition and run out and buy more RAM.

---

### Post by oldos2er on 2014-03-14
> **jackson21 said:**
> So it means that  I have to set up a 16 GB drive for swap.


Not at all. I have a desktop with 8GB RAM, and a 512MB swap file (not partition), which has never been used to my knowledge.

---

### Post by buzzingrobot on 2014-03-14
No specific rule for the optimum size of a swap partition exists.  If it did, we'd all be using it and installers would offer to set things up automatically.

If a machine has no swap partition and the amount of code and data that attempts to be loaded into memory exceeds the size of that memory , there's a very good chance that things will just stop until the user manages to close something.  If the machine does have a swap partition, chuncks of code and data will be written and read  to and from the swap file until the demand on RAM decreases. 

Adjusting the size of the partition may affect the number of disk accesses, but it can't work magic.  Writing to and reading from a drive is orders of magnitude slower than shuffling bits around in RAM.

---

### Post by jackson21 on 2014-03-15
Thank you very much !!

Greetings from jackson

Thanks to buzzingrobot  for help,

jackson

---

### Post by nbjarvinen on 2014-04-29
> **3rdalbum said:**
> Heck, 8 gigs of RAM is a ridiculously large amount for an ordinary desktop computer.
I have 16GB and while using Windows 7 it has crashed several times in a year because RAM filled up. Why 16GB? I have huge amount of programs opened at the same time and I just put my computer to sleep at nights, I don't prefer shutdown very often. Usually I use Win7 from 1 to 2 weeks without shutdown and Ubuntu 2-4 weeks without restart. (I hate to use Win7 since it makes my computer really, really slow in a week while Ubuntu feels almost fresh after 3 weeks.)

With Ubuntu it had hit twice almost 100% of RAM usage. I know there is cache etc which is removable but I'm surpriced if over 12GB of it is only cache since there was pair of virtual machines running, Chrome with about 150 tabs opened, blender etc memory consuming applications...

---

### Post by Dane_Jorgensen on 2014-04-29
Do these numbers apply with virtual machines?  I have a virtual machine with 8GB, and I've never run into a problem with only 512MB swap.

---

### Post by emk on 2014-10-06
> **3rdalbum said:**
> Swap is not compulsory. On an 8 GB machine, the only thing you'd want swap for is hibernation. If you don't hibernate the computer, or if you suspend the computer instead of hibernating it, you don't need any swap at all. Heck, 8 gigs of RAM is a ridiculously large amount for an ordinary desktop computer. I'd even say that I'm scandalized by the wastage, because probably half of your RAM will never be touched.

The 2.5x RAM capacity rule comes from years ago when computers came with 128 megabytes of RAM, and it's a *suggested maximum*, not a minimum. Any more than 2.5x RAM and you'll experience lower performance. Less doesn't hurt.

In short: If you hibernate, allow your RAM size plus 1 GB (for instance, if you persist with buying 8 gigs of RAM, have a 9 gig swap partition). If you don't hibernate, don't bother with swap. You can always change your mind later and add it if you start doing high-end scientific analysis.I would add that todays' browsers are greedy pigs with memory.

The last years, 4 GB was enough to get by without swap. Not anymore.  Chrome with less than a dozen tabs has repeatedly frozen my machine, I am setting up a 2 GB swap in this very moment. I suspect your recommendation to be true only for one more year.  A little swap partition can make the difference between being able to shut down offending programs or  to pulling the plug and losing unsaved work.

---

