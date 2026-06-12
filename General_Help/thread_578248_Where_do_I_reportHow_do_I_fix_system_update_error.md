---
title: "Where do I report/How do I fix system update error?"
date: 2007-10-17
forum: General Help
---

### Post by geoffBEAM on 2007-10-17
So I recently did a clean install of the Gutsy release candidate that hit digg a few days ago.

Everything is excellent except for this error when I try to run system update for:

**virtualbox-ose-modules-2.6.22-14-generic**
virtualbox-ose modules for linux-image-2.6.22-14-generic
From version 4 to 6 (Size 309 KB)


I get this error:

> E: /var/cache/apt/archives/virtualbox-ose-modules-2.6.22-14-generic_6_i386.deb: subprocess new pre-removal script returned error exit status 1


I did build virtualbox from source (my first compile success YEah), so this may have some bearing on the situation.

Any Ideas? That orange star appears to be mocking me. "You can install 1 update"  No.. I can't.

---

### Post by geoffBEAM on 2007-10-17
bump

---

### Post by LanDan on 2007-10-17
i love to buid from source myself.....but why???? its in the repos, just apt-get install virtualbox-ose

anyway, you can try to uninstall your source package by doing a "make uninstall" in the source directory

---

### Post by geoffBEAM on 2007-10-17
There was no uninstall script.  I did a manual uninstall using the files listed in synaptic, reinstalled with sudo apt-get update virtualbox-ose, now the orange star is no more.

Lesson learned! Thanks!

:KS

---

