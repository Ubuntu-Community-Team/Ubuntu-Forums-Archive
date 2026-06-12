---
title: "dev/hda2 has been mounted 30 times without being checked - What does this mean?"
date: 2007-01-18
forum: General Help
---

### Post by tc101 on 2007-01-18
I just got a message while booting up that said:

dev/hda2 has been mounted 30 times without being checked, check forced

and then it did some kind of test that took about a minute.  What happened and why?  Should I be doing something about this?

---

### Post by mcduck on 2007-01-18
Everything is fine. Linux usually automatically checks that your hard disks are fine. By default this happens every 30th boot.

---

### Post by dcstar on 2007-01-18
> **mcduck said:**
> Everything is fine. Linux usually automatically checks that your hard disks are fine. By default this happens every 30th boot.

You can change it to **n** duration and/or **n** mounts:
```
man tune2fs
```

---

### Post by RandomJoe on 2007-01-18
Going further, even though you are (probably) using ext3 - a journalled FS - it is possible over time for things to get "inconsistent" which can potentially lose data.  This is more likely if you are prone to killing the computer without proper shutdown, or if the power goes out while the system is running.  To be safe, by default ext2 and ext3 systems run a filesystem check every 'n'th boot (in this case 30) to be sure things are still good.

I think in 10 years of running Linux on ext2/3, I've had it actually find something during one of these just twice.  So it isn't a common issue, but I'd still rather deal with the check than lost data!  Only thing I might wish for is a prompt saying "it's been >30 restarts.  Shall I check?" in case it's a bad time - seems it wants to check right when I *need* the thing to start fastest! :rolleyes:   (Might have to look into scripting that...)

If it just took a minute, be happy!  You oughta see how long it takes my 1TB of drive space to check...! :mrgreen:

---

