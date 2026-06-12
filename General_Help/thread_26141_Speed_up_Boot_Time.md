---
title: "Speed up Boot Time?"
date: 2005-04-11
forum: General Help
---

### Post by mikearthur on 2005-04-11
I've looked through the wiki, and can't find anything.
Basically, I've moved to Ubuntu from Gentoo, and the only thing that bothers me is the ABSURDLY long boot time. Gentoo boots in, I reckon, about a quarter of the time. This may well to do with the LVM and RAID, for example, which do nothing on my system, services starting on boot.
Is there a guide/any tips to getting a lightning fast boot, without suspending to disk?
Thanks!

---

### Post by Nis on 2005-04-11
[QUOTE=mikearthur]I've looked through the wiki, and can't find anything.
Basically, I've moved to Ubuntu from Gentoo, and the only thing that bothers me is the ABSURDLY long boot time. Gentoo boots in, I reckon, about a quarter of the time. This may well to do with the LVM and RAID, for example, which do nothing on my system, services starting on boot.
Is there a guide/any tips to getting a lightning fast boot, without suspending to disk?
Thanks![/QUOTE]
 You can try installing the sysvconf package and use that to disable any unnecessary services.

---

