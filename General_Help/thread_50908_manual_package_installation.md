---
title: "manual package installation"
date: 2005-07-21
forum: General Help
---

### Post by ippiraman on 2005-07-21
I'm fairly new to Linux and I want to install xchm. I don't have internet access at home and I can only use one at a computer rental shop. My attempt to do sudo apt-get install xchm failed, so I decided to get the package manually from packages.ubuntulinux.org. I downloaded two files: xchm_0.9.7.orig.tar.gz and xchm_0.9.7-1ubuntu1.diff.gz but I have no idea where/how to put/install these files.

Many thanks.

---

### Post by Xian on 2005-07-21
It would be easier to download the [xchm_0.9.7-i386.deb](http://mirror.switch.ch/ftp/mirror/ubuntu/pool/universe/x/xchm/xchm_0.9.7-1ubuntu1_i386.deb) file and install it with dpkg.

---

### Post by damonw5 on 2005-07-21
[QUOTE=Xian]It would be easier to download the [xchm_0.9.7-i386.deb](http://mirror.switch.ch/ftp/mirror/ubuntu/pool/universe/x/xchm/xchm_0.9.7-1ubuntu1_i386.deb) file and install it with dpkg.[/QUOTE]
 To install with dpkg, "cd" to the directory you downloaded this file to and then in a terminal, type "dpkg -i ./xchm_0.97-i386.deb" . Unfortunately, that file probably depends on others you don't have installed, in which case you will have to install those first.

---

