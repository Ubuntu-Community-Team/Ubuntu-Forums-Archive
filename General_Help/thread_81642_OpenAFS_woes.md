---
title: "OpenAFS woes"
date: 2005-10-24
forum: General Help
---

### Post by a9dfasd9 on 2005-10-24
I really need to get the openafs client working on some breezy machines.  OpenAFS 1.4.0-rc3 works quite happily on a number of gentoo machines, however I haven't had any luck with ubuntu.  I've installed the openafs-client package plus it's friends (openafs-module-source) and built the module package (make-kpkg) openafs-modules and installed it.  The module seems to load okay (modprobe openfs gives no errors in dmesg) however it just doesn't work.  Nothing useful in the logs.  When I run "afsd" it says something about not being able to mount at /afs(22).

Please help.

Thanks in advance.

---

