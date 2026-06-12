---
title: "recover from boot disk failure with mdadm RAID 5"
date: 2008-06-13
forum: General Help
---

### Post by CAsurfer on 2008-06-13
I'm considering using mdadm RAID 5 on a 3 disk array. Each disk would contain an identical partition for the RAID setup. Additionally, one disk would have a partition for /boot as per [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461).

If the drive containing /boot dies, then the drivers/kernel which can read the RAID array will die as well. How would recovery be performed in this situation?

Thanks!

---

### Post by Happy_Man on 2008-06-13
Boot a live CD, reinstall, I guess. There's not much you can do if your kernels die on you. But that has an extremely low risk of happening.

---

### Post by CAsurfer on 2008-06-19
Yeah, it has about the same risk of happening as of a disk failing ;)

Of course, that's what redundant RAID is all about defending against...

---

### Post by fjgaude on 2008-06-19
AFAIK, you can't boot from a software raid5 array.

---

