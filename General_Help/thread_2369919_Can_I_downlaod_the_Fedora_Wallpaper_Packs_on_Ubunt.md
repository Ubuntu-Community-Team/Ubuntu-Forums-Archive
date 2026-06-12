---
title: "Can I downlaod the Fedora Wallpaper Packs on Ubuntu GNOME?"
date: 2017-08-28
forum: General Help
---

### Post by justint15 on 2017-08-28
Can I do commands like "sudo dnf install f25-backgrounds-extras-gnome" on Ubuntu GNOME without any problems?

---

### Post by vasa1 on 2017-08-28
No.

---

### Post by deadflowr on 2017-08-28
Generally, no.
Ubuntu uses the Debian package management system.
Fedora uses the Red Hat package management system.

Two things you can do are:
Download the binaries from the fedora repositories and then run [alien to convert]("https://help.ubuntu.com/community/RPM/AlienHowto") to deb packages.
or
Download the sources packages from the fedora repositories and [compile them and install from source.]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by QIII on 2017-08-28
dnf is the new package manager for RPM-based distros.  That is, Red Hat and family.  It uses .rpm packages.  Ubuntu uses apt, the Debian family package manager.  It uses .deb files.

---

