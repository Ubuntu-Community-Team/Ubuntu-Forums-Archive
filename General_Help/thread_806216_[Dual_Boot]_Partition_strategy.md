---
title: "[Dual Boot] Partition strategy??"
date: 2008-05-24
forum: General Help
---

### Post by kakyoism on 2008-05-24
Ready to install Hardy and WinXP on a 320G harddrive.
Here is my thinking,
3 partitions for WinXP in NTFS (i.e., system, applications, and temp)
1 partition for Ubuntu root, and 1 for swap.
1 data partition for both in NTFS

Does this scheme look OK?

A big question is:
I have 3G DDR2 RAM.
What would the recommended swap size of Ubuntu?
Is 1G enough? If I give it too much, say 10G, would my system
be more inefficient?

---

### Post by mikewhatever on 2008-05-24
Looks like a lot of NTFS partitions. The ones for Ubuntu are ok. 1 gb of swap should be more then enough unless you plan to suspend to disk, aka hibernate. With 3 gb of RAM your swap will probably stay idle most of the time.

---

### Post by strabes on 2008-05-24
That sounds good, but why do you need three partitions for windows XP? Seems kind of unnecessary to me. 20gb is plenty for my XP install.

20gb - NTFS Windows XP
15 - ext3 Ubuntu Root
Rest of HD - NTFS data storage

---

