---
title: "System doesn't start, /sbin/init: Accessing a corrupted shared library"
date: 2020-06-24
forum: General Help
---

### Post by azwrk on 2020-06-24
Hello everyone.
The problem that I have is this: Ubuntu Server 18.04 doesn't start.
The error is:

run-init: /sbin/init: Accessing a corrupted shared library
Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100

Before that the system would not load, it stopped at initramsfs.
I booted from USB and the target partition wouldn't mount.
I performed fsck on it, after that the partition could be mounted.
But the OS itself doesn't load, ends up with the Kernel panic error above.

Also if I try to chroot from USB:
chrooot failed to run command '/bin/bash': Accessing a a corrupted shared library

Is there a way to fix this or would it be easier to just reinstall the OS?

---

### Post by dino99 on 2020-06-24
Better starting with a fresh install from a fresh iso

---

### Post by Impavidus on 2020-06-24
You'd have to find out which packages got corrupted and reinstall all of them chrooted from the live disk. Probably easier to just reinstall everything. Note that random file corruption suggests a broken hard drive.

---

