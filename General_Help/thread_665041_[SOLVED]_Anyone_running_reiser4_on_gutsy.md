---
title: "[SOLVED] Anyone running reiser4 on gutsy?"
date: 2008-01-11
forum: General Help
---

### Post by Washer on 2008-01-11
Did it install successfully? I went through the normal steps

-installed linux sources for 2.6.22 plus a couple other dependencies

-added reiser4 patch for 2.6.22 (is it just me or are there a few versions running around?)

-added it as a module in menuconfig, did make deb-pkg, installed it, compiled initrd & changed menu.lst then booted from the new kernel.


It now mounts a reiser4 partition, but cannot write to it. Tried copying through the terminal & it returns a "segmentation fault" .. which makes no sense because fsck.reiser4 returns fine. I can make empty directories though. Seems like this should be an easy problem to fix, but I can't find anything.

---

### Post by Washer on 2008-01-12
ok this is nuts. I got make-kpkg to run, but I absolutely can't get past the segmentation fault. I think i'll let the file system fsck itself for a couple days :mad:

---

### Post by Washer on 2008-01-12
"Solved" by using vanilla kernel 2.6.23.13 with the reiser4 patch for 2.6.23-3. Normal steps.

---

