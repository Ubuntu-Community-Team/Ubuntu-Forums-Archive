---
title: "Permission trouble"
date: 2007-02-03
forum: General Help
---

### Post by bogdanb on 2007-02-03
Hi! This is a rather general Linux question, not particular to Ubunt -- though the answers can be Ubuntu-specific.

It's all about permissions: I have a large (500G) USB drive that I use to store pretty much all my data on. It's FAT32 formatted for good reasons (i.e., that can't change).

Because it often contains private data (photos, documents, etc), I always mount it with read permissions only for myself. However, some parts of it do contain data that is quite public, and I'd like to make it visible for other users, from guest logins to apache&samba.

However, I found absolutely no way of going around the mount permissions. As far as I can tell, it's all or nothing: either I let others read all the disk, or I forbid them reading anything at all.

Is there anything at all you can suggest? (Like I said, anything other than FAT32 is not an option.)

---

### Post by taurus on 2007-02-03
Why not partition the drive into two partitions:  one for your private use and one for public?

---

