---
title: "Couple ?'s about trackerd"
date: 2007-11-12
forum: General Help
---

### Post by posterboy on 2007-11-12
Upgraded from 7.04 to 7.10. Didn't notice, but trackerd runs by default. I don't want that. I am using beagle, and want to continue to do so. 2 questions: How do I stop it from running on boot, and how do I get rid of whatever it has indexed. It ran over night, so likely got a lot of stuff in a database somewhere. I'd love to kill that off. Thanks

---

### Post by justin_guerin on 2007-11-12
From what I can see of the tracker package, it doesn't run on boot, but upon login.  To stop it from running, remove /usr/share/autostart/trackerd.desktop and / or /etc/xdg/autostart/trackerd.desktop.  I'm not sure where it keeps its index, but if you want to get rid of it you could always purge the tracker package, as that will remove all files associated with the package.  Be aware that ubuntu-desktop depends on tracker, though, so you may have to manually select the dependencies of the metapackage.

Justin

---

### Post by posterboy on 2007-11-12
Thank you. I found it in both places, and removed it in both. However, the attempt to purge caused a great many dependencies to want removal also, like compiz, and all of it's stuff, ubuntu-desktop, as you thought, so, to heck with it, whatever disk space it is using I guess I can live with.

---

