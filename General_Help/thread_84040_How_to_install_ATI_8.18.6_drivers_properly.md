---
title: "How to install ATI 8.18.6 drivers properly?"
date: 2005-10-30
forum: General Help
---

### Post by Zingam on 2005-10-30
After I bumped my head against the wall for a few hours I got the ATI 8.18.6 drivers to work on Ubuntu 5.10 but I'm not sure if they are properly installed.
For example: the first time I have ran Quake 4 it was very choppy (with the same driver under 5.04 - gameplay was quite smooth). Later Quake 4 run fine but not as good as under 5.04, which could be a sound related problem.

One issue is that ATI control panned does not provide information about the driver as earlier, it just says: unspecified.
Also the driver does not want to use its internal gart functionallit because it conflicts with the one provided by the kernel. I had no such problem on Ubtuntu 5.04.


Any idea what's wrong? How can I disable the external gart kernel module?

Do you know how to install the drivers on a new Ubuntu 5.10 installation properly? Although I've managed to make them work, I have no idea exactly how.

Approximately I've done this:
I've installed GCC 3.4, GCC 3.3, libqt3, the default ATI 8.16 drivers, control pannel, restricted packages, etc. then I've unstalled them.

---

### Post by bionnaki on 2005-10-30
dont know
but this thread got my ati drivers working just great:
[http://www.ubuntuforums.org/showthread.php?t=76057](http://www.ubuntuforums.org/showthread.php?t=76057)

---

### Post by Zingam on 2005-10-30
Thank you! But this thread is how to install the 8.16.20 drivers, which I've done and I've had to replace them, because they do not work properly on my computer.

---

