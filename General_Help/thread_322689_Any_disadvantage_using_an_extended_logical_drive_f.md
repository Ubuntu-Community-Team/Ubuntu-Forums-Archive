---
title: "Any disadvantage using an extended logical drive for the Linux swap file?"
date: 2006-12-20
forum: General Help
---

### Post by sarc on 2006-12-20
I dual boot Ubuntu and WinXP (don't ask me why... darned device drivers!!!!) and I placed the Linux swap file in an extended logical drive I created with Windows (I needed 3 primary drives for some other good reason..).  Seems to run fine.  Any performance advantage to be gained by moving the swap file to a primary drive?  Thanks

---

### Post by kidders on 2006-12-21
Hi there,

Afaik there is, but it's probably very slight. Other factors, like the size of the partition, or the kernel's "swappiness" would have much more of an impact on performance, I'd say.

(My 2c!)

---

### Post by zgornel on 2006-12-21
No noticeable advantage.

---

### Post by az on 2006-12-21
> **sarc said:**
>   Any performance advantage to be gained by moving the swap file to a primary drive?  Thanks

None whatsoever.  A primary versus extended/logical partition makes no difference - the format is such because of the limitations of the MBR format but it's not like the HD has to look any harder to find the partition on the disk.  It's an appliance.

---

### Post by sarc on 2006-12-21
Thanks guys (and girls?)

---

