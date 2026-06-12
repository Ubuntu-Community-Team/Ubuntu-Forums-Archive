---
title: "Where do blkid and vol_id get their info?"
date: 2007-08-12
forum: General Help
---

### Post by Midahed on 2007-08-12
I'm trying to sort out some inconsistent UUIDs for my software raid devices.

I've tried all variants of the blkid command switches and have deleted /etc/blkid.tab and blkid.tab.old, but it insists on returning the 'wrong' UUIDs (compared with mdadm --detail) for my array devices.

This doesn't appear to cause a problem, but I'd like to understand where blkid and vol_id get their information from and, if possible, correct it so that it's consistent.

blkid and vol_id return the same incorrect UUIDs.

Thanks,

Mike

---

