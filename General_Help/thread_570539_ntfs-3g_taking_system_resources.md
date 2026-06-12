---
title: "ntfs-3g taking system resources"
date: 2007-10-08
forum: General Help
---

### Post by ZiVvmO on 2007-10-08
i've been having this problem intermittently lately.  since im running a laptop, i can hear every hard drive access quite clearly.  lately, i've been hearing a constant...scanning...i guess.  just continual hard drive activity.  when i bring up ksysguard and sort by cpu usage, the culprit is always mount.ntfs-3g.  it takes between 20 and 30% of cpu time when this happens.  its not really a problem cuz i can still do most everything without issue.  its just really annoying listening to it constantly hitting the hard drive for no apparent reason.

anyone know why/how to stop this?

---

### Post by prince_niceguy on 2007-10-08
ntfs-3g is the indirect problem i think. if you are having a desktop search or indexer working they might be scanning your ntfs drive and thus in turn resulting into this ntfs-3g to work on ntfs...

so, check out what is the real culprit...

---

### Post by szaka on 2007-10-08
Upgrade to NTFS-3G 1.1004 would probably help. There were a lot related major optimizations recently: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

---

### Post by ZiVvmO on 2007-10-08
> **szaka said:**
> Upgrade to NTFS-3G 1.1004 would probably help. There were a lot related major optimizations recently: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)
upon following the instructions in the thread linked to by the ntfs-3g site (which is a thread on this forum posted by givre) it tells me i have the most up-to-date version.  it seems the most recent version in the repositories is 1.328, and im scared to compile from source #-o

---

