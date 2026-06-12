---
title: "Alternate Data Streams..."
date: 2007-07-16
forum: General Help
---

### Post by cprofitt on 2007-07-16
I am curious if the LInux supported file systems have alternate data streams or anything similar.

Thanks.

---

### Post by dreadlord_chris on 2007-07-17
> **PrivateVoid said:**
> I am curious if the LInux supported file systems have alternate data streams or anything similar.

Thanks.

Sorta, they are called Extended Attributes and are present in ext2, ext3, and xfs filesystems (and others).

[http://acl.bestbits.at/about.html](http://acl.bestbits.at/about.html)

They do have some limitations, though, that aren't present in the MS ADS model - size of the data stream being a major difference.

---

