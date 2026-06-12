---
title: "synaptic and dependency management"
date: 2005-08-14
forum: General Help
---

### Post by doboy007 on 2005-08-14
Hi I'm new to ubuntu (and linux as a whole)

I'm wondering if anyone can tell me how to make synaptic (or some other ?console application) give me a list of all installed packages that are not dependencies of other installed packages - similar to FreeBSD's pkg_cutleaves. I want to delete old dependencies or old applications that I may have forgotten about.

Thanks in advance -

Doboy007

---

### Post by heimo on 2005-08-14
These may help:

[http://www.ubuntuforums.org/showthread.php?t=53176](http://www.ubuntuforums.org/showthread.php?t=53176)
[http://www.ubuntuforums.org/showthread.php?t=53150](http://www.ubuntuforums.org/showthread.php?t=53150)

---

### Post by doboy007 on 2005-08-15
Tried deborphan and synaptic. Unfortunately it doesn't provide a full list of non-dependencies.

---

### Post by heimo on 2005-08-15
[QUOTE=doboy007]Tried deborphan and synaptic. Unfortunately it doesn't provide a full list of non-dependencies.[/QUOTE]

I'm not 100% sure what you're looking for, but try installing and running orphaner on terminal. That's what I use.

---

### Post by doboy007 on 2005-08-16
Thanks - orphaner seems to do a better job as you can look for all packages, not just libraries.

---

