---
title: "Randomn FSCK behavour"
date: 2008-03-06
forum: General Help
---

### Post by AJB2K3 on 2008-03-06
Fsck keeps reporting thats it been 33 time since the file system was check problem is its randomly running on startup between 1 restart and 10 restarts?
WTF why is randomnly running but still reporting the same thing ?
How do I reinstall it/fixthis?

---

### Post by AJB2K3 on 2008-03-07
Please someone must be able to help?
:confused::confused::confused::confused::confused:

---

### Post by dcstar on 2008-03-07
> **AJB2K3 said:**
> Fsck keeps reporting thats it been 33 time since the file system was check problem is its randomly running on startup between 1 restart and 10 restarts?
WTF why is randomnly running but still reporting the same thing ?
How do I reinstall it/fixthis?

fsck will run after "x" mounts or if the filesystem was not shut down and unmounted correctly.

Boot up off a Live CD and manually run fsck on the hard disk partition that is causing the problem.

---

