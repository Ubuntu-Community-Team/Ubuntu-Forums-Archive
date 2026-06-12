---
title: "messing with init and runlevels"
date: 2006-07-16
forum: General Help
---

### Post by HAARP on 2006-07-16
Hi there.
One hopefully simple question:
How do I make a script load at bootup, **at a specific time**? It has to be loaded before @S35mountall.sh. I need this script executed in every runlevel (expect 0 and 6, of course)
Can just add another symlink with the corresponding number in rcS.d which points to the script I want executed? Are runlevel S scripts even used when booting into other runlevels?
Thanks

---

### Post by HAARP on 2006-07-16
S scripts are always used.
Thanks anyway.

---

