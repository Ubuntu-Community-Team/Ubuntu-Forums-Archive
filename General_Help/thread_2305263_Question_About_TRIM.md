---
title: "Question About TRIM"
date: 2015-12-04
forum: General Help
---

### Post by echotech2 on 2015-12-04
In cron.daily I have the line "/sbin/fstrim --all -- no-model-check || true".  I have separate "/" and "Home" partitions on the SSD.  Does this trim both partitions?  I suspect it does but just checking.

---

### Post by Linuxisfast on 2015-12-04
AFAIK, it does the entire drive.

---

