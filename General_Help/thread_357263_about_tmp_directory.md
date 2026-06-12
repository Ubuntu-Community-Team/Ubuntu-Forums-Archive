---
title: "about /tmp/ directory"
date: 2007-02-09
forum: General Help
---

### Post by Mateo on 2007-02-09
i want to know a bit about the /tmp/ directory.  here are a few questions:

1) who has permissions to modify it? just root?

2) is this directory cleaned out periodically by the OS?

---

### Post by dagnabit dang doohickey on 2007-02-09
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html")

---

### Post by Haegin on 2007-02-09
I recommend you learn more about permissions here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) and then use ```
ls -l / | grep tmp
``` to find out who owns /tmp. On my PC root owns it but anybody can read write and execute inside it so its basically open access.
Also it is cleaned out regularly - I think on reboot as I certainly don't have anything from yesterday in there.

---

