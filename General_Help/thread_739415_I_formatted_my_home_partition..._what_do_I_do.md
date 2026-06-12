---
title: "I formatted my home partition... what do I do?"
date: 2008-03-29
forum: General Help
---

### Post by Yes on 2008-03-29
I formated my home partition.  When I boot, it says "File system check failed.  Please repair the system manualy."  So I've copied all my files back to the home partiton from my backup, but it still won't boot.  What else do I need to do?

Thanks.

---

### Post by pointone on 2008-03-29
Formatting likely changed the UUID of the partition. You will need to edit /etc/fstab and change the UUID to match the output of "blkid".

---

### Post by Yes on 2008-03-29
That did the trick.  Thanks!

---

