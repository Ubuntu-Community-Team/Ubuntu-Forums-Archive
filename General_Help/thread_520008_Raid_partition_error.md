---
title: "Raid partition error"
date: 2007-08-07
forum: General Help
---

### Post by azray on 2007-08-07
I have 2- 80gb drives in a raid 1 array. One drive seems to have a partition error. Using gparted in terminal drive SDA shows; /dev/sda3 as unknown. The other raid drive (sdb) shows that partition as linux swap.

How do I fix this problem?

---

### Post by brent113 on 2007-08-07
If you're using mdadm (I assume you are) then I would try running a disk check and then rebuilding it rebuilding it.

I can't recall the exact commands to type, but the steps are to run e2fsck and then fail the drive, then rebuild the drive.

If you look those up in the man pages they have all the commands you need there.

---

