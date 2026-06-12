---
title: "Disk/OS maintenance"
date: 2004-11-10
forum: General Help
---

### Post by dubdubdub on 2004-11-10
Is there anything I should do to check the disk for errors or fix permissions? An application or command?

I am used to having to use Disk Utility in OS X for this type of mainteance.

---

### Post by fng on 2004-11-11
well, there is at least no gui, but there are some command line tools.

It all depends what partition scheme you are running.
ext2/3 -> e2fsch
reiserfs -> reiserfsck
xfs -> xfs_check
...

---

