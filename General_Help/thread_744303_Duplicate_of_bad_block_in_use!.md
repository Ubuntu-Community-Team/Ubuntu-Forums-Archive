---
title: "Duplicate of bad block in use!"
date: 2008-04-03
forum: General Help
---

### Post by jonbey on 2008-04-03
My pc was running slowly, so I decided to reboot (I use it as a server, so it is on all the time). 
Reboot failed. It did a disk check, as one had not been done for 180 days. But the check failed (this is copied from the screen, may have some errors):

Check failed:
Duplicate of bad block in use!
So I then did
fsck

which gave this:
Pass 1: Checking inodes, blocks and sizes

> Running additional passes to resolve blocks claimed by more than one inode....
Pass 1B: Rescanning...
Multiply-claimed blocks in inode 7: 8 16 73
Multiply-claimed blocks in inode 3387409: 73
Multiply-claimed blocks in inode 3452049: 1
Multiply-claimed blocks in inode 3452051: 8
Multiply-claimed blocks in inode 3452052: 16
Pass 1C: Scanning directories for indoes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 4 inodes containing multiply claimed blocks)

File /usr/src/linux-headers-2.6.20-15-generic/include/config/8139too/8128.h (inode #3387409, mod time Sun Apr 15 06:03:37 2007)
    has 1 multiply-claimed block(s), shared with 1 file(s):
             <The group descriptor inode> (inode #7, mod time Thu Oct 4 22:19:56 2007)
Clone multiply-claimed blocks<y>?


I said yes to this and then a few more.....

> Pass 2 through to Pass 5: Checking group summary information
Free blocks wrong for group #1 (29652, counted=29648)
Fix?


Which ends in 
> 
/dev/hda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda1: ***** REBOOT LINUX *****
/dev/hda1: 188463/4807488 files (1.1% non-contiguous), 4068761/9612886 blocks
root@computer:~#

So I reboot, but then get

> Could not start the X server due to some internal error. 



A bit lost now. So, I was thinking, maybe I will just reinstall - if I can recover my web files (not backed up for a while).

But - why has this ocurred? 

Should we run a disk check on a regular basis?

Can I fix this somehow?

Could the error have been caused by a security breach?

Confused. Worried. Tired.

Any advice greatly appreciated.

Cheers

Jon.

---

### Post by cdenley on 2008-04-03
I think there are two reasons filesystems usually become corrupt:

-not unmounted properly (power loss)
-hardware problem (bad hard drive or memory)

It is unlikely your filesystem would be corrupted as a result of a security breach.

---

### Post by jonbey on 2008-04-03
Thanks for that. Glad to update you - after a second reboot, it is working again. The fsck worked.

Really it could be any of the options you stated, although most likely not unmounted, as I was forced to hit the power switch when the whole system froze - and that may have been caused by a HDD problem...

---

