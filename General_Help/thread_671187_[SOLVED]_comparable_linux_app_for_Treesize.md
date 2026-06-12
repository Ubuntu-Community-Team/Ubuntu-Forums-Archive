---
title: "[SOLVED] comparable linux app for Treesize?"
date: 2008-01-18
forum: General Help
---

### Post by TechnoJunky on 2008-01-18
On my Windows computers I've used a program callled Treesize, which would examine the hard drives and let me know where all my disk space was being used.  It would say that these directories are in C and this is the size that each is taking, then you could drill down each directory and it would say the same for all sub-directories.  Is there anything similar for Linux?

---

### Post by gvartser on 2008-01-18
Open up a shell:
#) cd /
#) sudo du -H

Best regz,
/G

---

### Post by Sam on 2008-01-18
Applications / Accessories / Disk Usage Analyzer


It's installed by default.

---

### Post by TechnoJunky on 2008-01-19
Thanks guys.  I couldn't find the disk usage analyser (maybe it's a gnome product) so I decided to see if I could install it and found kdirstat.  This is exactly what I was looking for.

---

### Post by der_joachim on 2008-01-19
Try Filelight. It's a QT application and it is in the repos.

---

