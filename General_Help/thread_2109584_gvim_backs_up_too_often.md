---
title: "gvim backs up too often"
date: 2013-01-28
forum: General Help
---

### Post by hawthornso23 on 2013-01-28
Using gvim on my laptop is currently a painful experience as when not plugged in it tries to ... backup .... every ... single ... keystroke ... to disk. Which means every couple of seconds the disk spins up and vim ... waits ... because it wants to write its backup and then the disk spins down again. It is seriously disturbing my concentration when I'm trying to work.

Does anyone know how to tell it to only write a backup every 10 minutes or so.

---

### Post by hawthornso23 on 2013-01-28
OK - gvim wasn't the problem. It was ridiculously aggressive APM spinning the disk down almost as soon as it became inactive. This is actually harmful to the disk! I removed laptop mode tools and the problem has gone away. 

gvim still backs up quite frequently even on battery, but this now means an almost unnoticeable disk write every five or ten seconds,  and not a slow massive and wasteful spin cycle.

---

