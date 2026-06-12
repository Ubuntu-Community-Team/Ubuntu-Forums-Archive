---
title: "kern.log.1 25.3Gb in size?"
date: 2020-03-04
forum: General Help
---

### Post by schneil-2k on 2020-03-04
Hi all

I'm running low on disk space.
According to disk usage analyser, /var/log is taking up 35.2Gb of space
In particular kern.log.1 is taking up 25.4Gb.  Can any of these files be deleted?

thanks in advance

---

### Post by CatKiller on 2020-03-04
All of them. You'll probably want to check the new one to see what's been spamming the log so much. I mount /var/log as tmpfs so that nothing ever gets actually written, to save on SSD writes.

---

### Post by oldfred on 2020-03-04
I houseclean older logs as if no issues you do not need the older logs.
But if you have unusually large log, that does indicate some sort of issue.

Some older Asus needed boot parameter pci=nomsi to prevent run away log files.

---

