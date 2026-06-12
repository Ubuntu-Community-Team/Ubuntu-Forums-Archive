---
title: "How do I uninstall libre office"
date: 2015-11-03
forum: General Help
---

### Post by dellboy56 on 2015-11-03
How do I uninstall libre office please because this was installed from the Ubuntu installation I would like to completely remove it but how do I I'm tried sudo apt-get --purge libre office

---

### Post by howefield on 2015-11-03
Try

```
sudo apt-get remove --purge libreoffice*.*
```

Make sure to check the list of packages to be removed before confirming.

---

### Post by Mark_in_Hollywood on 2016-03-31
```
sudo apt-get remove --purge libreoffice*.*
```

shows it will uninstall gnome. 

Please state command and a way to NOT uninstall gnome.

---

### Post by Dennis N on 2016-03-31
gnome is a meta-package to provide the GNOME Desktop Environment, so removing it will not remove any packages installed for that environment.
See: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages) 

```
dmn@Sydney:~$ apt-cache show gnome
Package: gnome
Priority: optional
Section: universe/gnome
Installed-Size: 53
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: meta-gnome3
Version: 1:3.8+4ubuntu6

Description-en: Full GNOME Desktop Environment, with extra components
 This is the GNOME Desktop environment, an intuitive and attractive
 desktop, with extra components.
 .
 [B][COLOR="#FF0000"]This meta-package depends on the standard distribution of the GNOME
 desktop environment[/COLOR][/B], plus a complete range of plugins and other
 applications integrating with GNOME and Debian, providing the best
 possible environment to date.

```

---

