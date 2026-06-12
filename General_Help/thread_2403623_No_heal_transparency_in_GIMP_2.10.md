---
title: "No heal transparency in GIMP 2.10"
date: 2018-10-13
forum: General Help
---

### Post by adlerhn on 2018-10-13
I have GIMP 2.10 installed from the Cosmic repository. I also have installed the gimp-plugin-registry package, and I can see under /usr/lib/gimp/2.0/plug-ins a plugin-heal-transparency.py file.

However, I cannot see the "Heal transparency" filter in the menu. Also, in the plugin filter I don't see any plugin whose name contains "Heal".

Any advice of what could I try to get the filter to show?

---

### Post by nlee2 on 2018-10-14
Make sure that the plug-ins are in the Edit --> Preferences --> Folders --> Plug-ins folders location.

---

### Post by adlerhn on 2018-10-14
It turns out the gimp-python package is not available in the Ubuntu repository. I installed the package from [https://packages.debian.org/buster/amd64/gimp-python/download](https://packages.debian.org/buster/amd64/gimp-python/download) and the plugin works fine now.

---

