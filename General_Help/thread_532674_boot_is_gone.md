---
title: "/boot is gone"
date: 2007-08-23
forum: General Help
---

### Post by gabng on 2007-08-23
Hi, my /boot partition is dead.  Is there a way to reinstall /boot without reinstalling the whole system?  My / is still intact, only /boot is gone.  Please help!!

---

### Post by livestockPimp on 2007-08-23
I think you have to re-install, the kernel & bootloader sit here.
how is the partition missing? did you delete/format it?

---

### Post by gabng on 2007-08-23
Thx for replying.
I'm running my system on software raid, my / is mirrored, so when the HD died, there's still the other one and I can rebuild it.  However, my /boot is on its own partition on the dead HD, so when the HD died, the partition is gone...
So there's no other way to just install /boot???  If it's possible I'd like to put it together with / so it gets mirrored too...

---

### Post by livestockPimp on 2007-08-23
im not sure, i guess you could try doing a dummy install of the same distro w/ same kernel version and dumping your / in with it.

---

