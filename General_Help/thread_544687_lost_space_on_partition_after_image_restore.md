---
title: "lost space on partition after image restore"
date: 2007-09-06
forum: General Help
---

### Post by skullmunky on 2007-09-06
i tried cloning a drive using partimage.  it worked fine, with one exception:

the source partition is small, 24GB, from a multi-partitioned system. 

the target machine has the full 120GB for the root partition. 

after cloning, df -h / tells me the the partition is only 24GB; but gparted says it is still 120GB.   i know on the partimage docs it says restoring to a larger partition may lose "some" space, but i didn't think "some" meant "almost all!" 

is it completely fubared, or is it just that the ext3 filesystem is confused and could maybe be convinced that it now has more space?

---

