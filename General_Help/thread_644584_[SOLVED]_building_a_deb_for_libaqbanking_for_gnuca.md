---
title: "[SOLVED] building a deb for libaqbanking for gnucash"
date: 2007-12-19
forum: General Help
---

### Post by ryjax01 on 2007-12-19
I'm following the instructions from [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

I have followed the steps so far with no problems until I try to build the deb for libaqbanking.

I've modified the debian/rules to the following:

#!/usr/bin/make -f
DEB_DH_INSTALL_SOURCEDIR=$(CURDIR)/debian/tmp
include /usr/share/cdbs/1/class/autotools.mk
DEB_CONFIGURE_EXTRA_FLAGS := --disable-static --with-backends="aqhbci aqdtaus aqgeldkarte aqofxconnect" --with-frontends="cbanking g2banking"
...

I've modified the debian/controls and created debian/libaqbanking-ofx0.install as instructed

When building the deb, I get the following error:

 
...
dh_installdebconf -paqbanking16-qt-wizard
dh_installemacsen -paqbanking16-qt-wizard
dh_installcatalogs -paqbanking16-qt-wizard
dh_installpam -paqbanking16-qt-wizard
dh_installlogrotate -paqbanking16-qt-wizard
dh_installlogcheck -paqbanking16-qt-wizard
dh_installmime -paqbanking16-qt-wizard
dh_installchangelogs -paqbanking16-qt-wizard  ./ChangeLog
dh_installudev -paqbanking16-qt-wizard
dh_install -paqbanking16-qt-wizard --sourcedir=/home/ryjax/Projects/gnucash/libaqbanking-2.2.3/debian/tmp
cp: cannot stat `/home/ryjax/Projects/gnucash/libaqbanking-2.2.3/debian/tmp//usr/lib/aqbanking/plugins/16/wizards': No such file or directory
dh_install: command returned error code 256
make: *** [binary-install/aqbanking16-qt-wizard] Error 1
ryjax@homebox:~/Projects/gnucash/libaqbanking-2.2.3$


Has anyone else experienced this error before? I'm not sure why the folder/files for 16/wizard is not getting created. I think an option needs to be created somewhere; however, I have not been able to find what it is. Any help is greatly appreciated. Thanks!

---

### Post by ryjax01 on 2007-12-19
I found the problem. 

I took it upon myself to remove qbanking and kbanking from the DEB_CONFIGURE_EXTRA_FLAGS because I was only interested in g2banking.

It looks like that the plugins/16/wizards is created only when qbanking is included  in the --with-frontends option

So now my DEB_CONFIGURE_EXTRA_FLAGS line reads as follows:

DEB_CONFIGURE_EXTRA_FLAGS := --disable-static --with-backends="aqhbci aqdtaus aqgeldkarte aqofxconnect" --with-frontends="cbanking g2banking qbanking"

---

