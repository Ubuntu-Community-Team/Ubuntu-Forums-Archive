---
title: "Virtualization Question"
date: 2006-08-31
forum: General Help
---

### Post by tonyr1988 on 2006-08-31
When setting up a multi-booting computer, the #1 hardest thing for me was determining the partitions. How large should they be? You want enough space in your shared partition for all your files, but you need each OS to have enough space to store all the programs you need. Plus, it's a pain to grow / shrink them later.

I've been messing around with virtualization recently, and it's pretty cool. I was wondering if this would be possible:

-Setup your drive as one huge partition.
-Install the smallest OS possible. No GUI (or minimal), smallest possible consumption of RAM, etc. Just enough to:
-Run virtualization software. Install your OSes that way.

That way everything is one partition, and you don't have to worry about under-estimating your partition sizes. Make sense?

It would probably never work, but I'm just wondering what problems that would have (not that I plan on trying it on a computer I use anytime soon :P).

So please, shoot it down! (but be nice :D)

---

### Post by mejy on 2006-08-31
> **tonyr1988 said:**
> When setting up a multi-booting computer, the #1 hardest thing for me was determining the partitions. How large should they be? You want enough space in your shared partition for all your files, but you need each OS to have enough space to store all the programs you need. Plus, it's a pain to grow / shrink them later.

I've been messing around with virtualization recently, and it's pretty cool. I was wondering if this would be possible:

-Setup your drive as one huge partition.
-Install the smallest OS possible. No GUI (or minimal), smallest possible consumption of RAM, etc. Just enough to:
-Run virtualization software. Install your OSes that way.

That way everything is one partition, and you don't have to worry about under-estimating your partition sizes. Make sense?

It would probably never work, but I'm just wondering what problems that would have (not that I plan on trying it on a computer I use anytime soon :P).

So please, shoot it down! (but be nice :D)

Nice idea, but unfortunately there are a number of flaws with that idea.  Namely:

1.  The performance hit of virtualising an operating system - even without taking into account the host's footprint - is significant enough to make the solution undesirable.  You'd be running two layers of drivers, for a start.

2.  Most current virtual machines don't offer any easy way to resize virtual harddisks/partitions.

3.  To run a virtual machine on even the lowest foot print Linux system would require an X Server, which would mean you ended up with two X serverrs or an X server + the windows GUI running.

4.  You would not be able to get any 3D acceleration - emulating a 3D card is tricky business, and the only way to do it is with the experimental support built into VMWare Workstation 5, and it only works with windows as the guest OS.

5.  By far a better solution would be for all major file systems to be easily resisable and moveable.

In the future, when Xen becomes mainstream (Xen provides very efficient virtualisation), when graphics cards can be easily and efficiently virtualised, and when computers are fast enough that we don't need to worry about the performance hit, virtualisation like this could be great - for a start you could run as many OSs as you wanted at the same time.

---

