---
title: "Where are my files? (software installtion problem)"
date: 2008-04-05
forum: General Help
---

### Post by Jay I. on 2008-04-05
Hi! I just installed apache2.2.4 but cannot find where. I've got the same problems with other software installed via synaptic package manager. So where are my files? Does anyone know? Many thanks in advance.

---

### Post by chrisccoulson on 2008-04-05
```
dpkg -L apache2.2-common
```

Most applications you install via the Ubuntu repositories should install a desktop file, so you get a launcher in your menu. This way, you don't need to know where the files go. If you spot a package with missing launchers, report it on Launchpad. This won't be the case with server applications like apache though.

---

### Post by tubasoldier on 2008-04-05
The config files for apache are in /etc/apache
The default web directory is /var/www

Hope this helps

---

### Post by Jay I. on 2008-04-05
Thanks for help guys! Actually i was looking for apache configs but couldn't find them with find. Last month I installed apache on mandriva from source and most of the files were installed in /usr/local/apache2. I guess it's worth reading something about synaptic packages for me.

---

