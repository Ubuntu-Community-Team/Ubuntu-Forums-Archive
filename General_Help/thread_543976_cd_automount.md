---
title: "cd automount"
date: 2007-09-05
forum: General Help
---

### Post by Dilutu on 2007-09-05
Hi
Recently, both of my cd/dvd drives stoped automounting when I insert a disc.I also noticed that computer/places only shows cdrom0. Both drives are ok with winxp.I' m running Dapper.

---

### Post by Dilutu on 2007-09-09
To those who might have this problem, I googled a solution. Turns out that when you add or delete users via the gui of "users and groups", it screws the permissions for user hal and haldaemon.You have to guive them access to your cd  and floppy drives again!!!!! Thanks to that bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/26338](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/26338).

---

