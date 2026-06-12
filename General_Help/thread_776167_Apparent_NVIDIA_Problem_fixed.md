---
title: "Apparent NVIDIA Problem fixed"
date: 2008-04-30
forum: General Help
---

### Post by brickbat on 2008-04-30
Hi,

Just thought I would let people know what problem I appeared to have, what the problem actually was and how I fixed it.

I had 2 Ubuntu partitions both with 7.10.  The second one (The oldest partition) was upgraded via update manager.

When I rebooted, there were no 8.04 items in the boot list.  I thought nothing of it and booted through anyway.  At that point, nothing seemed to work properly.  The NVIDIA driver never installed no matter what I did.

Finally after a couple of days (I'm not the fastest cab off the rank), I remembered that I wasn't getting 8.04 items in the menu list so I checked to see what was up with that.  It turned out that it was using the boot system of the newer Ubuntu install which had not been updated during the install.

All I did was open a terminal and copy all the kernels and stuff from the updated boot folder to the actually booting boot folder.  Then I copied all the missing items from the updated menu list to the actually booting menu list.

Viola.  A properly working Ubuntu 8.04.

---

