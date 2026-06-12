---
title: "Strange File Permissions"
date: 2015-08-07
forum: General Help
---

### Post by jim_deadlock on 2015-08-07
I've just had to recover/repair a partition which is now mostly fine, but some of my directories are messed up:

```
s---r-x--T 1 2952696849 1554667510       0 Mar 28  1992 Bank
c--x--x--x  1 jim jim 163,   8 Aug 27  1967 Bowie
brwxr-xr-x  1 jim jim 169, 201 Dec 24  1976 ACDC
```

How can I reset these as normal directories?

---

### Post by NathanRodriguez on 2015-08-07
Looks like something gone wrong with the repair, what tool have you used ?

---

### Post by jim_deadlock on 2015-08-08
GParted from a 12.04 live disk - I resized the partition a bit and it became usable. It had become corrupted during a resize/move with a 15.04 disk which froze during the operation.

Is it necessary to run another repair on the entire partition just for a few directories? Surely I can use chattr or something to reset these directories? I'm wary about messing around with the partition again after the panic while it was broken.

---

