---
title: "SD card not recognized and unmountable?"
date: 2019-10-09
forum: General Help
---

### Post by francktheminer on 2019-10-09
Hey,
I've got a friend who asked me to recover the contents from a microSD card that appears to be dead, however I still have my hopes, but to be fair they're already thin enough for me to give up in a bit.
The device is recognized on an lsblk as it should, mounted in /dev/mmcblk0, reporting 8006MB total and 7636MB used, however the filesystem isn't recognized. I tried running a few commands like dd, ddrescue to create images, but dd didn't seem to output anything and probably just froze (I'm new to linux so I can't really tell when that happens), and ddrescue made at least 5 cycles and rescued 0 data. I remember running another command and it mentioning the fact that there was a superblock error, and I've read that's associated with ext file systems and because that card was used for photography and I highly doubt it was preformated on a linux pc, I'm assuming its either in ExFAT or FAT32, which gets me confused as to where it got the superblock error, although I have a feeling it might be exactly because the file system is missing so it defaults to ext.
Anyways any help is appreciated.
And yes, I only use this forum for SD-card related problem solving

---

### Post by TheFu on 2019-10-09
*He's dead Jim*.  Time to warp to a new planet.

---

