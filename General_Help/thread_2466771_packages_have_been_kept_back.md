---
title: "packages have been kept back"
date: 2021-09-05
forum: General Help
---

### Post by robert71 on 2021-09-05
When i do sudo apt-get upgrade i get the following errors: 

The following packages have been kept back: 
  gnome-shell-extension-desktop-icons-ng ubuntu-advantage-tools

is there a way to fix this ? 

Thank you for your help.

---

### Post by grahammechanical on 2021-09-05
The way to fix this is to wait. Packages are kept back to allow other packages that they are dependant on to complete the process of being upgraded and added to the software repositories. 

If this package were to be installed at this time it is likely that there would conflict between it and other parts of the system.

Regards

---

### Post by deadflowr on 2021-09-05
If using apt-get then the upgrade option does this, and you can try using the dist-upgrade option.
You can also use the apt command and upgrade will install those, usually.

```
sudo apt-get upgrade # this only updates packages already installed, will not install new packages

sudo apt-get dist-upgrade # this will install updates and new packages if required to do so in order to update the system as a whole

sudo apt upgrade # this will install updates and new packages, but has a caveat that it cannot remove existing packages if an update requires it to do so

sudo apt full-upgrade # this will install all updates and new packages as well as it can remove packages if an update requires that it do so
```

---

