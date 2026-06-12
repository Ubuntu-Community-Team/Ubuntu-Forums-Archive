---
title: "problem with suspend to disk -&gt; system crash"
date: 2008-03-11
forum: General Help
---

### Post by Mcihi on 2008-03-11
i tried to suspend my pc to hard disk (ubuntu 7.10 desktop) - but this didn't finish and the system came back up with a warning that the suspend-mode didn't work.

at the next reboot the system tried to check the root filesystem but failed to do so because of too many errors. so i booted a live-cd and corrected the errors (fsck.ext3) which removed some inodes (???).

no my system is back up running - but:

the file "/var/lib/dpkg/status" is gone - so the packet-manager is useless!!!
i cannot edit any settings in evolution anymore - that gives me a segmentation fault.

is there a way to recover the status file or a command that regenerates it?

also there seems to be a problem with shutting down now - the pc sometimes suspends to disk and sometimes shuts down...

---

