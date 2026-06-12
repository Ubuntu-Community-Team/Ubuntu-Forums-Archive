---
title: "How do I uninstall a package after compiling / installing it?"
date: 2008-06-22
forum: General Help
---

### Post by bpont on 2008-06-22
I just successfully compiled and installed Transmission 1.22 on my Gutsy box.

I may want to compile and install an updated version in the future, but before I do that, I would want to uninstall and clean out the old package and its remnants.  How would I go about doing that?

---

### Post by -grubby on 2008-06-22
```
sudo apt-get remove --purge transmission
``` should do it

---

### Post by mc4man on 2008-06-22
If you used make install to install then _maybe_ there's an uninstall script in your source/build folder. In that case sudo make uninstall will work (assuming you don't/haven't deleted that folder.) If there isn't you'll have to do it manually.
If you used checkinstall or built from a debian rules file then it was installed as a .deb and can be removed like any other .deb

---

### Post by Nepherte on 2008-06-22
If you installed it by doing make and make install, you can easily remove it again if you still have the source directory where you compiled it. Go to that directory and run sudo make uninstall. Otherwise you'll have to remove every file manually.

---

