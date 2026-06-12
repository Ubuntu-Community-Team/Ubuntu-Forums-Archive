---
title: "fsck.reiserfs out of disk space"
date: 2007-11-25
forum: General Help
---

### Post by Toe Knee on 2007-11-25
What to do when you run  "sudo fsck.reiserfs /dev/hdc4 --rebuild-tree" and get the error ".Not enough allocable blocks, checking bitmap...there are 0 allocable blocks, btw out of disk space"?

The partition was originally on  /dev/hda7 (mounted as /home) and was 99% full when it had an error.  I have bought a new HD and dd'd the partition to a bigger partition (nearly twice the size) then tried to  "sudo fsck.reiserfs /dev/hdc4 --rebuild-tree" but it still says it can't allocate blocks...

Any ideas?

Thanks,

---

