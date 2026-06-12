---
title: "how to delete lost+found folders"
date: 2008-04-28
forum: General Help
---

### Post by CorruptNoob on 2008-04-28
Hi, I have lost+found folders about 1gb big from a new install of ubuntu on a partition that used to be part of a bigger partition for windows, I didn't defragment the partition so I think that's where all the lost+found stuff has come from, anyway, I just want it deleted

How can that be done?

---

### Post by justleen on 2008-04-28
sudo rm -rf lost+found ?

edit: double double double check your current working dir and path which your are trying to delete when issueing any rm commands as root!

---

### Post by ryanhaigh on 2008-04-28
The lost and found folder contains files that were recovered during a disk scan, I would be VERY cautious about deleting them, the names might not be correct but you may find you are missing some files you want later.

---

