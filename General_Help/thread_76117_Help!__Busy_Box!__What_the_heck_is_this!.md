---
title: "Help!  Busy Box!  What the heck is this?!"
date: 2005-10-14
forum: General Help
---

### Post by antdengineer on 2005-10-14
As soon as Breezy final came out, i whiped clean my ubuntu partions and did a reinstall.  I was using hoary.  Everything was working fine.  It installed great, rebooted, and I was using it.  I then rebooted again and it failed to boot.  It boots into something called BusyBox and it says can't acess tty; job Controll turned off.  I have tried a reinstall.  Does the same thing :mad: Anyone have any suggestions?  Thanks

Anthony

---

### Post by antdengineer on 2005-10-15
I kind of figured out whats happening.  It seems that after an install, i can reboot as many times as I want and do whatever and It will work fine.  Its only after I have booted into windows and then back into breezy that this happens.  Anyone else having this problem?

---

### Post by wmcbrine on 2005-10-15
Is this only after a warm boot -- can you fix it by shutting down (power off), then back up, before you start Ubuntu? (Or by hitting Reset in between?) Or does it stay messed up across power cycles?

I used to have a system that would hang if I tried to warm boot into Linux after Windows, because of the way Windows initialized certain hardware. But that was a long time ago (I'm talking about a 486 here).

Oh, and to answer the subject: BusyBox is a program that incorporates a lot of small Unix utilities into one program, to save space. It's used mainly for very small distros (like the kind that fit on a floppy), or recovery disks. It's not something you'd normally notice; you'd just run, say, "ls" as usual, only "ls" would be a symlink to "busybox" instead of a separate binary.

[http://www.busybox.net/about.html](http://www.busybox.net/about.html)

I dunno how it's being used in this case. I don't have Breezy yet, and I don't see it in Hoary.

---

### Post by cocox on 2006-05-15
maybe this can help you

[http://ubuntuforums.org/showthread.php?t=174537&highlight=hdc+upgrade+breezy](http://ubuntuforums.org/showthread.php?t=174537&highlight=hdc+upgrade+breezy)

---

