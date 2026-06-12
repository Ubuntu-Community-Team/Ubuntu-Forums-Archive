---
title: "Data files for some packages could not be downloaded"
date: 2015-09-22
forum: General Help
---

### Post by Matrix01 on 2015-09-22
this message showed up while software updater was running.
how do you fix this?

---

### Post by Rex Bouwense on 2015-09-23
The message tells you exactly what to do.  Fix your internet connection and then remove and re-install the packages to fix this problem.

---

### Post by buzzingrobot on 2015-09-23
If you are sure your connection is OK, it might be that the server hosting the files the update was trying to download was offline at that moment. Running updates again is likely to resolve it.

That package does not contain Adobe Flash, but downloads it from an Adobe site and installs it.  

There is also a reinstall option to apt-get, which reinstalls packages that are already installed. So, you might try "sudo apt-get install --reinstall flashplugin-installer" in a Terminal.

---

### Post by Matrix01 on 2015-09-26
thank you,
plush plug in, is installed from a terminal.



> **buzzingrobot said:**
> If you are sure your connection is OK, it might be that the server hosting the files the update was trying to download was offline at that moment. Running updates again is likely to resolve it.

That package does not contain Adobe Flash, but downloads it from an Adobe site and installs it.  

There is also a reinstall option to apt-get, which reinstalls packages that are already installed. So, you might try "sudo apt-get install --reinstall flashplugin-installer" in a Terminal.

---

