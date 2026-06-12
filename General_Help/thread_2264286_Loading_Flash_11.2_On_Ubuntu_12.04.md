---
title: "Loading Flash 11.2 On Ubuntu 12.04"
date: 2015-02-06
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-02-06
How do I load Flash 11.2 on Ubuntu 12.04?  I get asked to pick an application to install it with,but none of the choices are helpful.

Thanks, Hannibal

---

### Post by Impavidus on 2015-02-06
Installing the package **flashplugin-installer** from the repositories? I think that did the trick on 12.04. I don't run that release any more.

---

### Post by coljohnhannibalsmith on 2015-02-06
Failure

Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flash-properties-gtk adobe-flashplugin
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 6,914 B of archives.
After this operation, 19.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse flashplugin-installer amd64 11.2.202.440ubuntu0.12.04.1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse flashplugin-installer amd64 11.2.202.440ubuntu0.12.04.1
  404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.440ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.440ubuntu0.12.04.1_amd64.deb)  404  Not Found [IP: 91.189.88.149 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
sophie@sophie-Inspiron-5520:~$

---

