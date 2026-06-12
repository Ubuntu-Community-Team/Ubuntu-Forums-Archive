---
title: "can't mount using the HFS or HFS+ file system...."
date: 2006-09-10
forum: General Help
---

### Post by Patrick-Ruff on 2006-09-10
hi you guys, I cannot mount a DVD using the HFS or HFS+ file system, it seems like I've tried everything, my friend burned me a disc w/ a mac and all that and theres a lot of HFS-based stuff on there that I cannot view...I've tried soo many commands and its ridiculous...it doesn't want to work...here's what I've tried so far.


```

sudo mount -t hfsplus /dev/sr0 /media/OSX (doesn't work, says the following)

mount: block device /sr/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0 missing codepage or other error

```

also tried that same command with hfs instead of hfsplus, no dice as well. I've tried modprobe'ing and all that, I have hfsutil installed, hfsplus, etc. it seems like EVERYTHING is installed that is needed to work....


can you guys PLEASE help me on this and don't let this thread just die out? I would REALLY appriciate it!

---

### Post by maxpower on 2006-09-26
I haven't tried it, but a google search pointed to hfsutils which is available through the repos.

mAx

---

