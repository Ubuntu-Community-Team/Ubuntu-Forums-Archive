---
title: "Restore"
date: 2008-04-16
forum: General Help
---

### Post by JPFX on 2008-04-16
Hi,
I am trying to install the restore packages (a backup program [www.restore.holonyx.com](www.restore.holonyx.com)).
When I run the command sudo apt-get install restore-ee it downloads the packages then starts installing them but fails with this errror:

dpkg: failed to write status record about 'libmono-corlib2.0-cil to /var/lib/dpkg/status: No space left on device.

Any help?

Cheers,
Daniel.

---

### Post by mmc on 2008-04-17
hi, the 'No space left on device' error is quite literal, it means your disk is full.

do a 'df -h' to see which partition area is full ( /var may be on / )

& if your in gnome you can use the 'disk usage analyzer' to find out whats taking up all your space ... once you clear some space the package should install ok

hope this helps

-mmc

---

