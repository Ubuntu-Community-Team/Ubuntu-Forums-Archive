---
title: "Trouble upgrading Hoary -&gt; Breezy (Can't remove cups)"
date: 2006-09-19
forum: General Help
---

### Post by kuroishi on 2006-09-19
I'm trying to upgrade to breezy and then dapper but it keeps locking up and it can't remove (nor can I manually remove) cupsys-driver-gnomeprint.  

```

root@ubuntu:~ # dpkg --remove cupsys-driver-gimpprint
(Reading database ... 89224 files and directories currently installed.)
Removing cupsys-driver-gimpprint ...
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 99!
dpkg: error processing cupsys-driver-gimpprint (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 cupsys-driver-gimpprint

```

This is preventing me from further upgrading my system.  Please help!

---

### Post by jago25_98 on 2006-09-30
bump! I get exactly the same error message

... until I enable debug in cups config file, then read log file and found it wasn't able to listen on 127.0.0.1:631 (couldn't bind),

so I disabled that in the cups config file and found that it no longer complained, but was still listening on 0:631,

but the KDE print manager is still freezing on initialising...

---

