---
title: "DIsk Full ClamAV Directory Huge!"
date: 2008-01-20
forum: General Help
---

### Post by Mojosdad on 2008-01-20
Had a few errors due to / partition filling up. No great problem can trim a few files, but noticed that /var/lib/clamav is occupying 870Mb of space. These are mostly directories whoc have begun to appear since last October (Gutsy upgrade time?) and have names like 'clamav-e77f6ef034b44b1bd814f82ef7155134'.

Does anyone know what these files are and why they have started to appear?

---

### Post by AlmaTlust on 2008-01-31
just found out that it fills my harddisk, too - did you find out what to do?
If not, I will probably try to move all the older stuff to the trashbin and look for a few days whether there are any errors, then delete it completely.

---

### Post by AlmaTlust on 2008-01-31
Well, I looked through the directory. The younger the subdirectories, the bigger. The youngest one is main.inc. So my conclusion: all the older ones are kind of backup versions which are obsolete.

---

