---
title: "Adventures with my RAID-1 /boot partition"
date: 2008-06-21
forum: General Help
---

### Post by BASICman on 2008-06-21
I'm running Hardy on a software RAID-1 in the following configuration,

[INDENT]
/dev/md0     /boot     64M
/dev/md1     SWAP      4G
/dev/md2     /         20G
/dev/md3               20G
/dev/md4     /home     425G     
[/INDENT]

All of these are RAID'd partitions. Well, after two Kernel updates, my /boot partition has filled up, and I would like to resize it somehow. Does anybody have any sort of idea how I could go about this?

(As an aside, does anyone know how I managed to fill up a 64M /boot partition with just two kernel updates...?)

---

