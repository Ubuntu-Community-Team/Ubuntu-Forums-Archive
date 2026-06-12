---
title: "convert a partition from reiserfs to xfs"
date: 2007-02-13
forum: General Help
---

### Post by Josef K. on 2007-02-13
I'm trying to convert a reiserfs partition into xfs, so I've umounted the partition then start gparted, deleted the old partition then create a new one
but gparted let me choose just ext\reiser\swap\fat32... no xfs option :confused: 
what should I do?

---

### Post by Crooksey on 2007-02-13
```
mkfs.xfs /dev/HDXY
```

To make a target partition XFS.

---

### Post by Josef K. on 2007-02-13
got it!
seems ubuntu by default don't install xfs support (xfsdump, xfsprogs) if you don't have an xfs partition when install the system
I had to install manually those 2 packages, then gparted was enough :)

---

