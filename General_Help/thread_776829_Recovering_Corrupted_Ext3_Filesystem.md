---
title: "Recovering Corrupted Ext3 Filesystem"
date: 2008-05-01
forum: General Help
---

### Post by sddfdds on 2008-05-01
My external hard drive lost power today, and when I turned it back on, it didn't mount because it was corrupt, and e2fsck complained about not finding the superblock.  I figured out where all the backup superblocks should be, but every single one failed with e2fsck.

So my first question:  Is it *really* possible for *all* the superblocks to get corrupted?  How often does that happen?

Having said that, when I do tune2fs -l on the drive (which i was doing to confirm the settings to figure out if mke2fs -n returned the right backup superblock locations) sometimes tune2fs says that it can't find any superblocks, but some random times, it returns the filesystem info, so there must be a superblock somewhere?  Is there a way to figure out which one tune2fs is finding?

And finally, what is the likelihood of getting data back using mke2fs -S?  Has anyone had any success with this?

Are there any other options for recovery that I'm missing?

Thanks

---

### Post by sddfdds on 2008-05-02
Update:

A friend recommened I use testdisk (in the repos) to check for the location of my superblocks.  It confirmed I had the right ones.  After running testdisk, e2fsck magically worked with the backup superblock and everything is fine now.

---

