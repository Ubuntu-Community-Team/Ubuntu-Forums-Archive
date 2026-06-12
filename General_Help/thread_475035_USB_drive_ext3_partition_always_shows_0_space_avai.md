---
title: "USB drive ext3 partition always shows 0 space available"
date: 2007-06-15
forum: General Help
---

### Post by guy.murray on 2007-06-15
Hi all,
     I have an ext3 partition on an external USB hard drive.  

Since upgrading to 7.04 I find that it always indicates 0 space available, even after deleting files, and will not allow me as user to add new files. However, it will let me add files as root, despite telling me there is no space available.

Can anyone tell me what could be causing this and if there is a way of repairing it, other than creating a new filesystem on the partition from scratch?

Many thanks

Guy

---

### Post by guy.murray on 2007-06-17
Gave up and did a mkfs ext3 on it. Now it doesn't show 0 space available. 

Niether, however, will it let anyone but root access it, nomatter how I set chmod!

Baffled

Worked fine in 6.10

Guy

---

