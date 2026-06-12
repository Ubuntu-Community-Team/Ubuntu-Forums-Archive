---
title: "Allocate more disk space to Ubuntu?"
date: 2008-02-29
forum: General Help
---

### Post by gogetadbl on 2008-02-29
I did a triple boot of Windows XP, Vista, and Ubuntu and now I am regretting the lack of space I gave my Ubuntu.  How do I find what large files are taking up all the space?  Also how do I allocate more space to Ubuntu and take unused space from Windows?  Is this safe? 

The main reason I need space is that I am running a tcl script that uses up tons of disk space while I run it.  So I figure my temp folder is huge somewhere.

EDIT: I realized the space that I am losing is /home space... am I supposed to be using /home for everything in general?  Is it possible to easily allocate from my Ubuntu filesystem to /home?

---

### Post by mytwobears on 2008-02-29
Yes, I allocated more disk space to Ubuntu by taking some away from Windows.  Download and burn the SystemRescueCD ISO from [here]("http://www.sysresccd.org/Main_Page").

Boot from the CD and use Gparted (which is on the CD) to reallocate the space.

---

### Post by gogetadbl on 2008-02-29
> **mytwobears said:**
> Yes, I allocated more disk space to Ubuntu by taking some away from Windows.  Download and burn the SystemRescueCD ISO from [here]("http://www.sysresccd.org/Main_Page").

Boot from the CD and use Gparted (which is on the CD) to reallocate the space.

I updated my post a bit.  Should I be using /home for everything (unless I want to be in root all the time)?  I only allocated 1gb to home but I have 6 gb in my Linux drive.  When I run my tcl script, my free space goes to 1mb since I use trace files.

---

### Post by gogetadbl on 2008-03-02
thanks for the help! I forgot that /home was its own partition....

---

