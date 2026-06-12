---
title: "Youtube stopped working after Udate this morning"
date: 2015-01-15
forum: General Help
---

### Post by daniell59 on 2015-01-15
Ubuntu 14.04 32

After this morning's update, Youtube no loner works in Firefox.
It does work however in Chromium. Any assistance will be appreciated.

---

### Post by Yellow Pasque on 2015-01-15
Close firefox and try reinstalling the package (give output of command if it doesn't work):
```
sudo apt-get install --reinstall flashplugin-installer
```

---

### Post by daniell59 on 2015-01-15
> **Temüjin said:**
> Close firefox and try reinstalling the package (give output of command if it doesn't work):
```
sudo apt-get install --reinstall flashplugin-installer
```

Thank you! It is now working.

---

