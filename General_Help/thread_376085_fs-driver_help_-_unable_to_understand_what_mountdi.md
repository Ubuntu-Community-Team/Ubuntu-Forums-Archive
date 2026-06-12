---
title: "fs-driver help - unable to understand what mountdiag says"
date: 2007-03-04
forum: General Help
---

### Post by navneeth on 2007-03-04
> 
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.10 software did not
mount it because there is at least one incompat feature flag set. The Ext2
IFS software does not implement:
* needs_recovery *
Here we have an Ext3 file system which has transactions left in its journal. A
pure Ext2 driver must not access such a volume which is in that state (to
prevent data loss!).
You may solve it by mounting it on Linux (which has a kernel with Ext3
support). Be sure that you cleanly dismount it, before you shutdown Linux.
After that the Ext2 IFS software should be able to access the volume.

I installed fs-driver, and when I tried to access my Ubuntu partition, I was asked whether to format it or not. I obviously did not want to do that. So, as per the instructions on their site, I ran this mountdiag thing, and the result is pasted above. I don't understand anything. :confused: 

I have problems logging into Linux, and hence I installed this software to salvage some files from my home directory.

Please help.

---

### Post by navneeth on 2007-03-04
Anyone?

---

