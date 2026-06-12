---
title: "how to upgrade a package installed with make"
date: 2007-02-07
forum: General Help
---

### Post by nephish on 2007-02-07
lo there,
i installed a program here while back with the ./configure | make | make install
went really smooth, now there is an update for this package that fixes a bug. 

is there anything i need to do before i remove the package ?

do i need to remove it at all ? or can i just install over the top of it with make install on the new package ?

if i do need to remove it, how do i do so ?

thanks

---

### Post by zekopeko on 2007-02-07
i think that you can just make | make install it again over the old version.

try to use sudo checkinstall. that generates a deb package and then you can remove it with synaptic

---

### Post by nephish on 2007-02-07
man, that was fast. i posted a few minutes ago, thanks.

ok, checkinstall instead of make | make install 
or still run make then do checkinstall ?

---

### Post by taurus on 2007-02-07
Have to run make first (after ./configure, of course) before checkinstall.

---

### Post by dannyboy79 on 2007-02-07
i would suggest making a copy of any config files that you might have customized. (smb.conf for example if you're uninstalling samba or like proftpd.conf if you're uninstalling or upgrading proftp), rename the file or put it in your home folder to keep it secure. (this way if the update installs a similar file, you can copy and paste or just rename the new 1 to something-original and then rename the old one (with all your settings from the previous install) to have the correct name and you should be good to go so that all your settings are still there even though you updated to the newer package.

then you're going to want to remove it and then retreive the new source and then install the new source. i suggest you use sudo checkinstall though, this will create  a deb for you to install so that when you want to remove it, you can simply do sudo aptitude remove packagename and sudo aptitude purge packagename instead of sudo make uninstall which sometimes doesn't work if the programmers didn't enable them. if that were the case, then you'll just have to find everything and delete it. See why checkinstall is so cool. here is a link to help you out. [http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually](http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually)

good luck.

---

### Post by nephish on 2007-02-07
worked great, thanks. And thanks for the link.

---

