---
title: "Openoffice refuses to open from (or write to) NFS volumes"
date: 2006-12-18
forum: General Help
---

### Post by ronzo on 2006-12-18
Openoffice refuses to open files from (or to write files to) NFS volumes. I think it is the problem solved in that posting: [http://lists.freebsd.org/pipermail/freebsd-questions/2005-November/104863.html](http://lists.freebsd.org/pipermail/freebsd-questions/2005-November/104863.html)

Where can I alter these settings in Ubuntu?

---

### Post by ronzo on 2007-01-08
Changing

export SAL_ENABLE_FILE_LOCKING

to

#export SAL_ENABLE_FILE_LOCKING

in /usr/lib/openoffice/program/soffice fixes the problem for me.

---

### Post by gyst on 2007-03-08
But then you have no locking. Better to get NFS locking working.

I switched my old (woody) server from nfs-user-server to nfs-kernel-server. Reboot. That fixed it.

---

