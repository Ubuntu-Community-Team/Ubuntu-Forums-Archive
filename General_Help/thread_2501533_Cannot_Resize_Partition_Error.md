---
title: "Cannot Resize Partition Error"
date: 2024-10-11
forum: General Help
---

### Post by gregacom on 2024-10-11
Can someone help me. I can't to merge partition from Unallocated from sda4 to sda1. I Want to move 966 MiB to sda1 ?

[https://photos.app.goo.gl/CDwRicXv2rCQ7BQm9](https://photos.app.goo.gl/CDwRicXv2rCQ7BQm9)


[IMG]https://photos.app.goo.gl/CDwRicXv2rCQ7BQm9[/IMG]

---

### Post by QIII on 2024-10-11
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2492924](https://ubuntuforums.org/showthread.php?t=2492924), which is now closed.

---

### Post by yancek on 2024-10-12
It might be possible but it is impossible to tell from the Gparted image you posted.  You need to run sudo fdisk -l and check the output to show the sectors.  In order to do this the partitions would need to be contiguous.  If sda1 and sda4 are contiguous, the basic process would be to first unmount all the logical partitions, those numbered 5, 6 and 7 then resize sda4 by moving it to the right.  This should have the unallocated space outside any partition and you should be able to move sda1 to the right to include the unallocated spae.  Make sure sda1 is not mounted.   If you are not sure, yYou could post the output here and someone should be able to tell you.

---

