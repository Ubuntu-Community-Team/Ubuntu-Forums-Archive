---
title: "Reinstall KDE from shell?"
date: 2014-02-16
forum: General Help
---

### Post by MobiusJedi on 2014-02-16
So, I somehow managed to uninstall some element of kde while removing wallpaper packages.
Kubuntu doesn't boot in normal or recovery mode.
I've tried to google a solution to no avail.
 I've tried apt-get install kwin (from root in Recovery, after enabling networking) and received the message that the package could not be found.

Any ideas?

(Kubuntu 12.04 installed on a laptop with wireless networking only.)

---

### Post by Erik1984 on 2014-02-16
The package for kwin is named "kde-window-manager"

---

### Post by MobiusJedi on 2014-02-16
Cool. That package is already there, apt-get build-dep is downloading dependencies now, so hopefully that's all I need to do.

---

### Post by MobiusJedi on 2014-02-16
Ok. Now, doing a recovery boot, I get "initctl: event failed."

---

### Post by MobiusJedi on 2014-02-16
Followed a suggestion elsewhere to install kubuntu-desktop. Fixed.

---

