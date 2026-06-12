---
title: "merging partition"
date: 2007-06-24
forum: General Help
---

### Post by thaibox on 2007-06-24
I installed Ubuntu and ran a dual-boot for a while, then I deleted the partition containing Vista thinking that I would be able to merge that space with my Ubuntu partition.

Now I have 50 gigs unallocated before my Ubuntu partition that I can't seem to do anything with.  I want to merge it all.  Any advice?  I finally have my OS the way I like it with everything working so I really don't want to just redo the whole thing.

Thanks

---

### Post by detroit/zero on 2007-08-18
I have somewhat the same issue. I have a dual-boot laptop with Vista on it, When I first got the computer I split the hard disk 50/50, half for ubuntu and half for Vista.

Being that Vista is the flaming crap-pile that it is, I rarely use it. I have since scaled back Vista to 32GB-ish and I either would like to

**A)** Extend my ext3 Ubuntu partition into the unallocated space; or
**B)** Create an extended partition to move my personal files into so that they are stored separate from the OS, making re-installs less worrisome.

Here's an image of my GParted screen to give you an idea of the layout:
[http://img371.imageshack.us/img371/3240/screenshotdevsdagpartedxf8.png](http://img371.imageshack.us/img371/3240/screenshotdevsdagpartedxf8.png)

When I try to unmount sda3 (my ext3 ubuntu partition) I get the following error message:
[http://img371.imageshack.us/img371/1825/screenshotgpartedvd2.png](http://img371.imageshack.us/img371/1825/screenshotgpartedvd2.png)

I assume this is because it's the partition I'm currently running out of, and will have to do any of this sort of modification while not inside the OS?

In any event, when I try to make the unallocated space into it's own partition, I get this error:
[http://img371.imageshack.us/img371/6163/screenshotgparted1ln7.png](http://img371.imageshack.us/img371/6163/screenshotgparted1ln7.png)
and can go no further because creating an extended partition doesn't seem to be an option inside GParted?

Should I use fdisk for that? Something else?

Ideally, I'd like a combination of both my attempted endeavors here.. maybe 20GB to back up my personal data and then merge the remaining space into the ext3 sda3 partition. I keep hitting roadblocks, though.

Any help is much appreciated.

---

### Post by merlinus on 2007-08-18
Use gparted live cd.  No probs with mounting or unmounting, and you can resize from either end.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Cochise on 2007-08-18
if you have an ubuntu cd boot from that and open firefox and go to [www.getdeb.net](www.getdeb.net), install the newest gparted from that. then open gparted and rezise your ubuntu partition.

---

