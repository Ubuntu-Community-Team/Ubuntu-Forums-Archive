---
title: "Bad Grub, or bad disk?"
date: 2007-01-04
forum: General Help
---

### Post by deebus on 2007-01-04
I had edgy installed on a desktop system, and it experienced some problems booting up recently.

Sometimes I would get the "Boot disk failure..." message from the BIOS, but after a few restarts, it would magically work.
This went on for a couple weeks or so, until finally it would start exhibiting different behavior:  upon boot-up, it would stop at the "GRUB loading..." stage.  Only, it wouldn't say what grub usually says.  I would get a black screen with the word "GRUB" in the upper left hand corner, and just freeze there. :confused: 

Bootable livecds work like a charm, of course.

I booted into the edgy livecd, and attempted to reformat the drive entirely.  When the GUI drive partitioning tool started, the process failed.  Of course, it being GUI, I didn't really see any kind of output detailing the nature of the failure.  I actually attempted this three times, each time with the same result.  ](*,) 

What is the general opinion on this?  Has my quasi-new 200GB hard drive crapped out already, or is there something far more sinister at work? :-k

---

### Post by bodhi.zazen on 2007-01-04
Sounds like a hardware problem to me ....

Can you boot the HD from the live CD ?

---

### Post by budgie9 on 2007-01-04
It sounds as if it could be a couple of things going wrong. 
1. The IDE controller  on the m/board playing up. 
2. The hard disk itself failing.
Can you try the following if you have already scrapped off your files.
Try formating the disk from DOS it will normally indicate there are disk errors and tell you so.
Use a Windows disk if you have one. 
Or use the  mkfs /dev/drive  command in Linux.

These should all at least show you something is wrong if there is, with the disk itself. You can format many times if you wish, as this will if there are any bad blocks help stablise the drive, if it is possible.   
If you suspect it is a Grub error then there are many posts relating to those here.

---

### Post by deebus on 2007-01-04
> **bodhi.zazen said:**
> Sounds like a hardware problem to me ....

Can you boot the HD from the live CD ?

Yes, good question; forgot to add that in the original post.  The livecd, once booted, can read the contents of the drive just fine.

I will try the mkfs command...


p.s.  thanks for the quick response, guys!

---

### Post by bodhi.zazen on 2007-01-04
When you boot the live CD you have an option to boot from the first HD.

---

