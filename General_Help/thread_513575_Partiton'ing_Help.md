---
title: "Partiton'ing Help"
date: 2007-07-30
forum: General Help
---

### Post by Yaffle on 2007-07-30
Hello,
I want to have linux and windows on a dual boot and I would like to have a /home partition which can be used in linux and windows, The problem Is that I do not know what will be best for me to do, and also i would like to try new file systems instead of having just one ext3 partition.

Here is my plan:
-- 80GB Hdd
---- 10 GB (Windows) (nfts)
---- 10GB (Linux (/) ) (reiserfs or XFS)
---- 55GB (W&L (/home) ) (ext3 or nfts) (Driver)
---- 1GB (Swap)

Can anyone help improve?

Thanks, :guitar:

---

### Post by brettg on 2007-07-31
Check out;

[http://swik.net/ntfs3g](http://swik.net/ntfs3g)

Keep your stuff on an NTFS partition and get R/W access to it from Linux

all the necessary packages are in the Ubuntu repo's (you may have to enable Universe & multiverse first)

---

