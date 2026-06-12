---
title: "Maintaining exact copy of hard drive as a backup"
date: 2007-06-09
forum: General Help
---

### Post by MindFork on 2007-06-09
After a lot of searching and reading, I still need help on this one.

I have ubuntu installed on an 80 gig hard drive, which is /dev/sda1

I installed another 80 gig hard drive and partitioned it exactly like the original.  It is /dev/sdb1 and is mounted as /media/disk on sda1

I am looking for a way to copy *all* of the files from sda1 to sdb1 and to maintain an exact mirror on the second drive so that if the first one fails, all I have to do is boot from the back up and everything keeps working.

I am looking for something *automated* that can do the file matching nightly.  I also am a massive linux noob so I need something with a GUI.  If it can only be done via scripts and command line functions, I will need pretty explicit instructions.

Any guidance is greatly appreciated.

---

### Post by ramjet_1953 on 2007-06-09
I use Ghost for Linux (G4L)

It is a stand-alone CD that has the ability (amoung other things) to make an exact 1:1 copy of a HDD.

I just bought another drive for my laptop, placed it in one of those small USB enclosures and use it to back-up everything on a regular basis.

It even copies GRUB, so a changeover only takes a few minutes.

Regards,
Roger :cool:

---

### Post by MindFork on 2007-06-10
Thanks Roger, that sounds promising.  Can it be scheduled to run on a nightly basis?  

> **ramjet_1953 said:**
> I use Ghost for Linux (G4L)

It is a stand-alone CD that has the ability (amoung other things) to make an exact 1:1 copy of a HDD.

I just bought another drive for my laptop, placed it in one of those small USB enclosures and use it to back-up everything on a regular basis.

It even copies GRUB, so a changeover only takes a few minutes.

Regards,
Roger :cool:

---

