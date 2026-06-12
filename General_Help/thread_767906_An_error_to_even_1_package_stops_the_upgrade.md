---
title: "An error to even 1 package stops the upgrade"
date: 2008-04-26
forum: General Help
---

### Post by Mateo on 2008-04-26
Upgraded via DVDrom.  gets about 1/3 the way through then get this error message.  It cannot be fixed, and prevents all of the other packages from installing.  So right now I have a 1/3rd complete upgrade.  Afraid to turn off or restart my computer for fear of the consequences.  Completely and totally unfixable.

```
Unpacking replacement human-theme ...
dpkg: error processing /cdrom//pool/main/h/human-theme/human-theme_0.18_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver
Errors were encountered while processing:
 /cdrom//pool/main/h/human-theme/human-theme_0.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Mateo on 2008-04-26
bump.

---

### Post by Mateo on 2008-04-26
Those with this problem do:

sudo dpkg --purge gnome-screensaver 

then when the upgrade is finished reinstall gnome-screensaver.

---

