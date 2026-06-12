---
title: "fsck threw an error at me at boot-time"
date: 2007-01-16
forum: General Help
---

### Post by matthias_k on 2007-01-16
Hi,

I'm using Linux for like 3-4 years now, but today was the first time fsck reported a disk failure when booting my PC. The message was something like: "Error reading from block XYZ due to a short read" (whatever that may be). It canceled the bootup process and left me with a root shell, where I should manually run fsck again.

I did that, and this time it found no errors. Still, do I have to be concerned? What causes these kinds of errors?

Thanks.

---

### Post by Jylrdnikon on 2007-01-31
i have a very simular problem. after i get root and run fsck it says i have the error still and askes to force rewrite, so i ran fsck with -y  yes to all,  and it will go for a long time and then freeze and i cant get a full scan with fsck.  anyone have any idea what the cause is?

---

### Post by jfca283 on 2007-01-31
maybe this could help
[http://ubuntuforums.org/showthread.php?t=347914](http://ubuntuforums.org/showthread.php?t=347914)

---

### Post by dcstar on 2007-01-31
> **Jylrdnikon said:**
> i have a very simular problem. after i get root and run fsck it says i have the error still and askes to force rewrite, so i ran fsck with -y  yes to all,  and it will go for a long time and then freeze and i cant get a full scan with fsck.  anyone have any idea what the cause is?

If you system "freezes" when reading a particular hard disk location then you could well have a faulty hard disk.

The system may not actually be "freezing", it could be just waiting for a faulty block to time-out and be in a loop where it tries multiple times and has to wait for each attempt.

---

