---
title: "[SOLVED] Canonical commercial repo doesn't work?"
date: 2007-12-12
forum: General Help
---

### Post by Dave_Man on 2007-12-12
Hi, 

For some reason the canonical commercial repository doesn't work for me.
It gives me the following error:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz)  404 Not Found


The line in my sources.list file:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

Anybody know whats wrong?
Thanks.
Dave.

---

### Post by p_quarles on 2007-12-12
Yeah, they changed the name of that repository in the new distro. Change "gutsy-commercial main" to "gutsy partner."

---

### Post by Dave_Man on 2007-12-12
Thanks a lot for the very quick response!
works now.

Dave.

---

