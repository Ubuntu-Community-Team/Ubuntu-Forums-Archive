---
title: "Update Manager wants to remove Gnome-shell"
date: 2013-06-01
forum: General Help
---

### Post by valotas on 2013-06-01
I've updated to 13.04 about a month ago. But know the update manager asks me to partially update to 13.04 and remove gnome-shell and install some new packages which include unity stuff. Is this normal?

---

### Post by cariboo on 2013-06-01
Moved to General Help, as this isn't a question about Saucy.

---

### Post by deadflowr on 2013-06-01
No, on a stable release, it's not normal for the updater to offer a partial upgrade, unless something major is happening.
You could provide the output for
```
sudo apt-get dist-upgrade
```

But don't click on the option for yes or no (y/n), or only mark it no.(n)

The output above should list remove, install, and upgrade.

But when a partial upgrade like the one you're getting wants to remove a package, it usually means a newer version is going to be installed.

---

