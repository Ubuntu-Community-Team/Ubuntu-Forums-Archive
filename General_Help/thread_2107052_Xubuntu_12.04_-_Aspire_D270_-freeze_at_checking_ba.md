---
title: "Xubuntu 12.04 - Aspire D270 -freeze at checking battery state."
date: 2013-01-20
forum: General Help
---

### Post by aselus on 2013-01-20
installed from USB, logged in once, and applied all updates, on reboot, freeze at "checking battery state. [OK]".


any help would be greatly appreciated <3

---

### Post by Toz on 2013-01-21
Did the updates include an update to kernel 3.5? You might want to have a look at these:
- [http://ubuntuforums.org/showthread.php?t=2074161]("http://ubuntuforums.org/showthread.php?t=2074161")
- [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031")

To rule out the kernel issue, hold down the shift key while booting and select a previous (3.2x) kernel.

---

