---
title: "Boot Problem"
date: 2005-07-07
forum: General Help
---

### Post by BigCdaAnswer3 on 2005-07-07
Everything on my laptop has been running fine with Ubuntu except out of nowhere I got this error at boot time:

root (hd0, 0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz root=/dev/hda1 ro console=tty0 queit splash
    [Linux bzImage, setup=0x1600, size=0x135b19]
savedefault
boot
.
Decompressing Linux...done.
Booting the kernel.
audit(1120743309.591:0): initialized
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

The weird thing is I never even changed any settings or anything-- it just stopped working yesterday...if anyone has seen this before or has been able to treat it w/ a live-cd, could you please share some knowledge? I've never actually used a live cd to diagnose any problems but I'm guessing this is what needs to be done.

Also I don't have any other kernels I can boot into  :(
i'm running 2.6.10-5-amd64-generic if this helps

---

