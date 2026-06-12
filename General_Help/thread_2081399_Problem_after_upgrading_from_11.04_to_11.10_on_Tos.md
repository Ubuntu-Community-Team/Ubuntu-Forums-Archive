---
title: "Problem after upgrading from 11.04 to 11.10 on Toshiba netbook"
date: 2012-11-06
forum: General Help
---

### Post by bryan.sailer on 2012-11-06
I upgraded my netbook and now it does not boot. After attempting to boot in recovery mode and running fsck I get the following information:

mount: mount point does not exist
mountall: mount [413] terminated with status 32
mountall: Filesystem could not be mounted:
mountall: Skipping mounting  since Plymouth is not available
fsck from util-linux 2.19.1
WARNING: bad format on line 8 of /etc/fstab
[   14.582349] Adding 2084860k swap on /dev/sda5. Priority:-1 extents:1 across:2084860k

What do I need to do to fix this? I have attempted to modify /etc/fstab but I cannot get into rw mode. I have tried this from the root shell.

---

### Post by bryan.sailer on 2012-11-06
After finding out how to remount my / in rw mode I was then able to modify the /etc/fstab and now the problem is fixed. That is what I love about Linux there is always away.

---

