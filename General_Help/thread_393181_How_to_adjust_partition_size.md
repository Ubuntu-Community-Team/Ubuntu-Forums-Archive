---
title: "How to adjust partition size?"
date: 2007-03-25
forum: General Help
---

### Post by Trebuchet on 2007-03-25
I'd like to shrink the ext3 partition and enlarge the ntfs partition. Can this be done with gparted? Is this possible? The Resize button is grayed out, but it must be able to do it under some circumstances.

---

### Post by floke on 2007-03-25
You can't resize partitions moving from right to left with GParted - so if your NTFS is on the left and ext3 on the right then you might be out of luck.

---

### Post by Trebuchet on 2007-03-25
Rats. Yes, the ntfs is to the left of the ext3 partition. Is there another Linux-compatible partition manager that might work? (I can't afford Partition Magic 8.)

---

