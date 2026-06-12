---
title: "dosfsk not allowing to write to disc"
date: 2014-02-20
forum: General Help
---

### Post by jdr2 on 2014-02-20
Trying to dosfsck (find fix errors) on an external hardrive. Any suggestions?

$ sudo dosfsck -av /dev/sdb
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Logical sector size (1766 bytes) is not a multiple of the physical sector size.
$ sudo dosfsck -av /dev/sdb1
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 0.&#65279;

---

