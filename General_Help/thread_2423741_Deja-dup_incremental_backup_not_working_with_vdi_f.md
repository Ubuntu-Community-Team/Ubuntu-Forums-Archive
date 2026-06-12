---
title: "Deja-dup incremental backup not working with vdi files"
date: 2019-07-28
forum: General Help
---

### Post by collin2012 on 2019-07-28
I love how easy is to recover a file using deja-dup and the nautilus file explorer method. But after a complete backup is made, the process get stuck on the vdi files. I read on other post like 2 or 3 topics that the workaround was to insert as ignore the location of the vdi files and use an alternate solution to back them up.
I would love to use one tool that fits all, and due to I use vdi on a regular basis, deja-dup has me looking around for troubleshoot ideas.

Do anyone has found a way to have incremental backups on vdi files using deja-dup?

---

### Post by TheFu on 2019-07-29
I don't know of any backup tools that are effective with 2GB files and larger.  I think it is a limitation with the librsync capabilities to diff large files.
 
The solution I came up with was to treat all VMs like physical machines and back them up using normal backup methods, effectively ignoring any huge files.  My backups are much faster this way.

---

