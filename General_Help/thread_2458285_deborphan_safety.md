---
title: "deborphan safety?"
date: 2021-02-20
forum: General Help
---

### Post by rsteinmetz70112 on 2021-02-20
Looking for a way to clean up a messed up upgrade I recently discovered deborphan which is supposed to detect orphaned packages.  That is packages that have "no packages depending on them." "The default operation is to search only within the libs and  oldlibs  sections to hunt down unused libraries."

I also discovered that you can use apt to remove all orphaned files.

```
apt-get remove --purge `deborphan` 
```

I'm wondering how safe that is. Running deborphan on one of my computers produces this list of packages;

```
# deborphan
**gnome-themes-standard**
libsctp1
ttf-dejavu-core
**dconf-tools**
libgcrypt11
libaugeas0
libsysfs2
libparted0
librpcsecgss2
activity-log-manager-control-center
pyotherside
libreoffice-presentation-minimizer
**grub2**
libdns21
overlay-scrollbar-gtk2
ttf-ancient-fonts-symbola
gnupg-agent
libapt-pkg4.12
libusb-0.1-4
lib32gcc1
qtdeclarative5-test-plugin
libelfg0
```

I don't know what most of them do. I assume libraries without any dependencies are pretty much useless. Others may simply be standalone packages that if removed could cause problems.
The highlighted packages seem like they might be needed and possibly some others might be as well.

---

