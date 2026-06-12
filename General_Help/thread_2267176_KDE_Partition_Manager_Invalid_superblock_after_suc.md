---
title: "KDE Partition Manager: Invalid superblock after successful move and resize."
date: 2015-02-28
forum: General Help
---

### Post by uh20 on 2015-02-28
I was trimming some space off of my linux and giving it away to windows when KDE partition manager gave me an error describing my superblock as unreadable.
It appears to have successfully moved my entire linux to the right a few MB (in order to fit on an extended partition) and then shrunk it down to the size it promised it would shrink it too.

here is the whole output from start to error:
[http://pastebin.com/sYHg75W4](http://pastebin.com/sYHg75W4)

Since i know the exact locations of my partitions at start and the translations/end, I am particularly interested about any way one can reformat a superblock backup to reflect on these changes.

Steps I have already taken included trying out all the backup superblocks and trying to find hidden blocks with testdisk

my backup is close to 3 months old and i would rather recover what should still be an ok filesystem than to lose 3 months and be forced to reinstall everything.

---

