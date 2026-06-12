---
title: "HDD not mounting correctly"
date: 2007-11-17
forum: General Help
---

### Post by one_million_facets on 2007-11-17
Hey all:

I've got a 500GB HDD that I'd like to mount for multimedia storage.  I've created the directory and gone through all the necessary cfdisk-ing (one partition formatted as "linux" option 83 which I assume is ext3) and fstab-ing.  But when I mount it, it only displays a capacity of 435GB.... LOST: 65GB of valuable storage that I paid for.  If found please return to..... Any ideas?

Much appreciated

---

### Post by taurus on 2007-11-17
If you are using ext3 filesystem, 5% of the space is reserved and by the way, 500GB doesn't mean it's really 500GB.

---

