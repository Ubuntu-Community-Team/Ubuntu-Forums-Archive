---
title: "Package installation from Kubuntu 8.04 CD"
date: 2008-06-14
forum: General Help
---

### Post by Alberto2 on 2008-06-14
Hello,
Due to some problems I'm now without a network manager and can't connect to the Internet, so, by the Kubuntu 8.04 installation CD , I tried to install **knetworkmanager**. So, first of all, in the sources.list I enabled the cdrom line, then by **apt-cdrom add** I tried to install it, but at the end of the process I obtained: "Impossible to open the file /var/lib/apt/lists/Kubuntu%208.04%20 ...... (13 Permission denied).
How can I obtain the permission to do that?
Best Regards

---

### Post by EmanresuusernamE on 2008-06-14
Type sudo before you do apt-cdrom add.

sudo apt-cdrom add

---

