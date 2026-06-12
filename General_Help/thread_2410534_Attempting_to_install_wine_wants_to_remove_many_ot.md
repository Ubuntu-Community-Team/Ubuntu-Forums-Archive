---
title: "Attempting to install wine wants to remove many other packages"
date: 2019-01-16
forum: General Help
---

### Post by stafio on 2019-01-16
Running Kubuntu 18.10, when I do ```
sudo apt-get install wine
``` in a terminal, the following comes up:
```
The following packages were automatically installed and are no longer required:
  apache2-data apache2-utils fonts-hack git-man kpart5-kompare libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libcolorcorrect5 liberror-perl libgit2-27 libgpgme++2v5 libgps23 libjs-modernizr libkf5texteditor-bin libkomparediff-data libkomparediff2-5
  libkompareinterface5 libmbedcrypto1 libmbedtls10 libmbedx509-0 libqalculate6 libqalculate6-data libtaskmanager6 php-composer-ca-bundle php-composer-semver php-composer-spdx-licenses php-composer-xdebug-handler php-psr-log php-symfony-console php-symfony-debug
  php-symfony-filesystem php-symfony-finder php-symfony-polyfill-ctype php-symfony-polyfill-mbstring php-symfony-process plasma-browser-integration plasma-integration python3-pyqt5.qtmultimedia python3-pyqt5.qtopengl python3-pyqt5.qtsvg python3-pyqt5.qtwebkit
  python3-qtpy qml-module-org-kde-kholidays qml-module-qtwebengine xxdiff
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  fonts-wine libcapi20-3 libodbc1 libosmesa6 libwine ocl-icd-libopencl1 php5.6-fpm php7.2-fpm wine64
Suggested packages:
  libmyodbc odbc-postgresql tdsodbc unixodbc-bin ttf-mscorefonts-installer q4wine winbind winetricks playonlinux wine-binfmt dosbox libwine-gecko-2.47 wine64-preloader
Recommended packages:
  wine32
The following packages will be REMOVED:
  apache2 apache2-bin composer git git-cola gitk kate kde-runtime kdelibs-bin kdelibs5-plugins kinfocenter kompare ktexteditor-katepart kubuntu-desktop libapache2-mod-php5.6 libapache2-mod-php7.2 libeditorconfig0 libkf5texteditor5 libkhtml5 libkjsapi4 libkjsembed4
  php-json-schema plasma-desktop plasma-widgets-addons plasma-workspace sddm-theme-breeze
The following NEW packages will be installed:
  fonts-wine libcapi20-3 libodbc1 libosmesa6 libwine ocl-icd-libopencl1 php5.6-fpm php7.2-fpm wine wine64
0 upgraded, 10 newly installed, 26 to remove and 0 not upgraded.

```

I would like to install wine, but I can't seem to do it without removing a number of packages that I use and are also core to my desktop environment. Is there some way around this?

---

### Post by dragonfly41 on 2019-01-16
One option to consider is to forego wine and instead [install windows in VM in VirtualBox]("https://itsfoss.com/install-windows-10-virtualbox-linux/").

---

### Post by Impavidus on 2019-01-16
I wonder if that long list of autoremovable packages has anything to do with those packages to be removed, as there are several dependency links between them. Maybe some packages have been marked for removal.

Let's see if anything strange is going on.```
dpkg -l | grep -v '^rc \|^ii '
``` will list all package in a strange state.

---

