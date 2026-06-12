---
title: "Data Recovery on a reiserFS partition, free software?"
date: 2007-05-25
forum: General Help
---

### Post by wconstantine on 2007-05-25
Anyone know any free data recovery software that can recover old files from a FAT filesystem? I'm currently using reiserFS on it. After the Ubuntu installation I realized I had some files that I needed from the fat filesystem!

Anyone? Please help!

---

### Post by ruy_lopez on 2007-05-25
sleuthkit & autopsy are particularly good:

[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/)

Also check out "foremost", which tries to recover files by their headers. Success of foremost usually depends on how fragmented the volume is.

---

