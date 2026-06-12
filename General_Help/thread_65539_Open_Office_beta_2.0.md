---
title: "Open Office beta 2.0?"
date: 2005-09-14
forum: General Help
---

### Post by gordonbp on 2005-09-14
Has this been put on a repository yet? (As opposed to Beta 1.9?)

Thanks

---

### Post by Zotova on 2005-09-14
Nope, as far as I know it is still 1.9

If you want beta 2 the best way I have found is to download the debs files and install those yourself.

---

### Post by gordonbp on 2005-09-14
Thanks. Where do I get the deb files from and is there a HOWTO about installing them?

---

### Post by Zotova on 2005-09-14
[This File](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/OOo_SRC680_m125_cs_native_LinuxIntel_install_deb.tar.gz) contains all the deb files you will need to install open office 2 beta 2

Also if you want to install a local language the files are [available here](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/OOo_SRC680_m125_native_LinuxIntel_langpacks_deb/)

Once you have downloaded the first link extract the files. Then in terminal install each of the deb packages.

To do that use:

sudo dpkg -i xxx.deb

xxx being the name of the deb file.

Use that command for every deb file including the local language files if you need them.

Also I got warnings about dependancy issues which worried me at first - however once all the deb files are installed these issues are resolved.

There is also a script in [this thread](http://ubuntuforums.org/showthread.php?t=30866&page=1&pp=10&highlight=openoffice). However personally I never had any joy using the script and found installing the debs manually a lot easier.

Hope that helps :)

---

