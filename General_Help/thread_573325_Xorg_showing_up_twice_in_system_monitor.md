---
title: "Xorg showing up twice in system monitor?"
date: 2007-10-11
forum: General Help
---

### Post by Hal.9000 on 2007-10-11
Lately I've noticed that every time I start up my computer Xorg is showing up twice in the System Monitor (screenshot attached).  Both entries are using the same amount of memory but only one is using any cpu, I have only noticed this as of late and I recently switched to the new ati (fglrx) driver 8.41.7 I was wondering why this might be happening and if it is because of the new driver.  Thanks

---

### Post by dcstar on 2007-10-11
> **Hal.9000 said:**
> Lately I've noticed that every time I start up my computer Xorg is showing up twice in the System Monitor (screenshot attached).  Both entries are using the same amount of memory but only one is using any cpu, I have only noticed this as of late and I recently switched to the new ati (fglrx) driver 8.41.7 I was wondering why this might be happening and if it is because of the new driver.  Thanks

In a terminal, do
```
ps -ef | fgrep processid
```
of the one that does not consume CPU, then you can see what process spawned it and repeat the command to follow the chain to see what kicked it off.

---

