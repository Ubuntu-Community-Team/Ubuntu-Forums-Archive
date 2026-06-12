---
title: "&quot;read-only file system&quot;  -  I am stuck"
date: 2007-05-14
forum: General Help
---

### Post by Audio_1 on 2007-05-14
I upgraded from 6.10 to 7.04.  I now am unable to delete files and whatnot, i get a message saying "read-only file system", both my drives are like this.  somebody said look at  /etc/fstab   so here it is.  Please remember, i am basically a noob with this thing.

[http://paste.ubuntu-nl.org/20883/](http://paste.ubuntu-nl.org/20883/)

also, it is possible that is is something completely different?

---

### Post by taurus on 2007-05-14
You can only read with ntfs driver.  If you want to write (and delete) files from ntfs filesystem, you need to use ntfs-3g.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

