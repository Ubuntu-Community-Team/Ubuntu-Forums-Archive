---
title: "[SOLVED] chkdsk runs on every startup- booting takes ages"
date: 2007-10-22
forum: General Help
---

### Post by Rimfrost on 2007-10-22
Hi,
Just installed 7.10 and it seems to be working OK apart from some minor issues. One problem that I do have is that when the system boots, it always run chdsk on my Windows partition which takes about 3-4 minutes, making booting painfully slow.
It also runs on my root partitition, but that only takes seconds. 
Does anyone know how to disable chkdsk from checking the window partition and just run on the root partition?

Regards,
Anders

---

### Post by aidanr on 2007-10-22
```
gksudo gedit /etc/fstab
```

look for the line relating to your windows partition and change the pass number to 0 (the last number on the line)

---

### Post by Rimfrost on 2007-10-23
Thanks! 
Works better now.

---

