---
title: "Upgrading from 6.06 LTS"
date: 2007-01-22
forum: General Help
---

### Post by sardopsycho on 2007-01-22
I am running 6.06 LTS fully upgraded and would like to upgrade to 6.10 - I remember reading somewhere that I can set Ubuntu to download and install the new release automatically.  

Can someone point me to those directions so I can perform that task once I get home from work?  

Thanks in advance!!

---

### Post by housam on 2007-01-22
I prefer the clear install. but if you want to upgrade, this is the best way to do it.
 [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by cmost on 2007-01-22
I second the recommendation to do a fresh installation.  There have been many, many reports of upgrades from 6.06 to 6.10 borking your entire system at worse or causing weird errors and other system wide issues after the upgrade at best.  Backup your home directory and do a fresh, clean install.

---

### Post by az on 2007-01-22
The gksu "update-manager -c"  should take care of many pitfalls in upgrading.  Unless you have a lot of foreign (non-package manager installed) applications, there is no reason to do a fresh install.

That is the simplest way to go.

---

