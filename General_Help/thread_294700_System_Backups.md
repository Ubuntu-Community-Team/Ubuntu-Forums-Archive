---
title: "System Backups"
date: 2006-11-07
forum: General Help
---

### Post by JackRazz on 2006-11-07
I want to know if it's possible to do a full system restore (including vmlinuz) from within my ubuntu desktop installation.  Currently, I boot up a SLAX Linux off a USB memory stick and do my backup/restores from there.  Do any of the gui backup programs do full system restores from within the OS itself?  I don't believe that a backup program is included on the ubuntu CD to do restores with, unless I run a bash script.

In a similar vein, Windows has System Restore and Apple's new Leopard will have Time Machine.  What about snapshots? Is there a filesystem like zfs or xfs that people would trust with their filesystem on a ubuntu desktop and server?



Thanks - JackRazz

---

### Post by kidders on 2006-11-07
Hi there,

> **JackRazz said:**
> I want to know if it's possible to do a full system restore (including vmlinuz) from within my ubuntu desktop installation.  Currently, I boot up a SLAX Linux off a USB memory stick and do my backup/restores from there.
Call me unadventurous, but I would continue doing that, personally. I know it's a pain, but when dealing with important data, I prefer it if there's no margin for slip-ups. Having said that, the only reason I've ever needed to do a system restore was when my OS was completely b0rked ... so being able to do it from inside the install itself would have been pointless. Out of interest, can I ask what other circumstances would warrant rewinding your life to the last backup?

I know that's not really what you want to hear, but maybe someone else will offer a more constructive suggestion :-)

> **JackRazz said:**
> Is there a filesystem like zfs or xfs that people would trust with their filesystem on a ubuntu desktop and server?
Most filesystems are equally trustworthy. By and large, the choice comes down to which set of optimisations you feel apply best to your own situation.

---

### Post by JackRazz on 2006-11-07
Hey kidders,
Thanks for vote of confidence for the current method (just had to get this in on election day).  I'm currently on a linux learning curve.  When I can't fix whatever it was I did...It came in handy a few days ago when I was getting a *Failure to Initialize HAL* error and wasn't sure what caused it (see [here]("http://www.ubuntuforums.org/showthread.php?p=1714229")). I now know that simply installing PostgreSQL caused it.  Still have it and don't know why.

If I were to recommend Ubuntu to other desktop users, I know they would not be willing to use the method I'm using for full backups.  Microsoft and Apple have drop-dead simple ways and I was hoping there was one for Ubuntu.  That's why I was looking for an easier method.  ZFS's snapshots could solve this, but it be a good while (if ever) before linux gets this.

JackRazz

---

