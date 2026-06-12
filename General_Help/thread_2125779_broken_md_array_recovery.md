---
title: "broken md array recovery"
date: 2013-03-15
forum: General Help
---

### Post by lvm on 2013-03-15
Synopsis: while md array was reshaping from raid5 to raid6 computer froze and had to be powercycled. The freeze was caused by a static discharge - I've tried to remove a USB flash stick, got a hell of a spark and that's that. Not that it probably matters, but someone got to be curious :) After specifying the backup file md assembled the array and continued the reshape but filesystem (xfs) is now broken - mounts but displays lots of invalid files and directory entries, at a glance over 50% files are damaged.

When the reshape will finish I am going to run checkarray and then xfs_repair. Any brighter ideas? I googled a lot but found very little about the recovery of md arrays after they've been assembled, apparently everyone assumes that once it is assembled it is going to be fine, and it isn't.

---

