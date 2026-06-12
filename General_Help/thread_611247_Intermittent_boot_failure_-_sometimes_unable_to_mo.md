---
title: "Intermittent boot failure - sometimes unable to mount root filesystem"
date: 2007-11-12
forum: General Help
---

### Post by cadnr on 2007-11-12
After upgrading to Gutsy from Breezy (via Dapper and Feisty) I am now having intermittent boot failures on my Acer 5562 laptop because the root filesystem is not being mounted.

Sometimes (about one in four boot attempts) the root filesystem is not found so that /proc etc. can't be mounted and the system drops me to the initramfs prompt. The rest of the time the system boots perfectly.  

The laptop is reasonably new so I have no reason to suspect a hardware problem, and the disk fscks okay.  I have tried the Dell solution in [http://ubuntuforums.org/showthread.php?t=558001&highlight=intermittent+boot+failure](http://ubuntuforums.org/showthread.php?t=558001&highlight=intermittent+boot+failure) and also tried reinstalling the kernel image, to no avail.

---

### Post by cadnr on 2007-11-13
Bump

---

### Post by cadnr on 2007-11-14
Can nobody give me a clue as to why this might be happening?

I suspect it has something to do with a driver not loading in time for the filesystem on the disk to be found... does that make any sense?

Is reinstalling Gutsy from scratch likely to fix it?

---

### Post by cadnr on 2007-11-16
Bumpetty bump for the final time, though I expect I must give up and relinquish to the life of dark uncertainty associated with intermittent boot failure ;.(

---

