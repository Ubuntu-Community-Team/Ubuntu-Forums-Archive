---
title: "Rescue mode - read only"
date: 2007-10-12
forum: General Help
---

### Post by coolclassic on 2007-10-12
I have just edited my fstab file by adding- defaults,noatime,data=writeback to root filesystem. Now my system does not boot, I have tried rescue mode to edit fstab but this is read only. How do I write to fstab in rescue mode. I have tried mc and vi.

---

### Post by thirddeep on 2007-10-12
Boot with CD, then mount that partition in read / write mode.

Thd.

---

