---
title: "Bad Blocks in my Hard Disk"
date: 2005-06-17
forum: General Help
---

### Post by galactus51 on 2005-06-17
Hi guys, I have a hard disk with bad blocks. When I try to mount the partiton ext3 (hda3 and hda4): kernel Panic. I have four partitions on disc, ReiserFS (hda1), Swap (hda2) and ext3 (hda3 and hda4). Just the ext3 partition is bad.
So, there is any Linux program to fix this problem? Or any other way to copy the files without change HDs ?
Please, forgive my bad english.

---

### Post by intangible on 2005-06-20
Have you tried this?:
**e2fsck -c /dev/hda3**
and
**e2fsck -c /dev/hda4**

---

