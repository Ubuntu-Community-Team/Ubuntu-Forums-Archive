---
title: "Can not update due to ' /var/lib/apt/lists/lock'"
date: 2019-09-07
forum: General Help
---

### Post by DougieFresh4U on 2019-09-07
Trying to update and this messege appears.
```
E: Could not get lock /var/lib/apt/lists/lock. It is held by process 2620 (packagekitd) - open (11: Resource temporarily unavailable)
E: Could not open file descriptor -1
E: Unable to lock the list directory
W: Be aware that removing the lock file is not a solution and may break your system.
```
Any help on what it is and how to fix would really be great.

---

### Post by Bashing-om on 2019-09-07
DougieFresh4U; Hello -

Only one instance of package management may be active at a given time.
Is process 2620 (packagekitd still active ?
If it has completed the lock should now be removed.
Try to update at this time -

[INDENT]I expect it now runs
[/INDENT]

---

### Post by SeijiSensei on 2019-09-08
Rebooting should fix this problem as well.

---

### Post by DougieFresh4U on 2019-09-09
> **SeijiSensei said:**
> Rebooting should fix this problem as well.
Yes rebooting did solve.
Sorry to have bothered with such a 'simple' issue. 
I should've know better.
Thanks

---

