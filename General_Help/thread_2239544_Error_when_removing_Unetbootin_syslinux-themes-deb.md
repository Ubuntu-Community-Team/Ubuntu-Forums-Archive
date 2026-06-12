---
title: "Error when removing Unetbootin: syslinux-themes-debian"
date: 2014-08-14
forum: General Help
---

### Post by kev9982 on 2014-08-14
Earlier today I attempted to uninstall the program Unetbootin, and received this error during the process.  

> 
installArchives() failed: (Reading database ... (Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 253949 files and directories currently installed.)
Removing extlinux (3:4.05+dfsg-6+deb8u1) ...
Removing syslinux-themes-debian (12-3) ...
/var/lib/dpkg/info/syslinux-themes-debian.postrm: 15: /var/lib/dpkg/info/syslinux-themes-debian.postrm: extlinux-update: not found
dpkg: error processing package syslinux-themes-debian (--remove):
 subprocess installed post-removal script returned error exit status 127
Removing syslinux-themes-debian-wheezy (12-3) ...
Removing unetbootin (585-2ubuntu1) ...
Removing unetbootin-translations (585-2ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Errors were encountered while processing:
 syslinux-themes-debian




Is there a way I can clear out the remaining package, or should I bother with it?  Can this error cause problems if left unresolved?

---

### Post by kev9982 on 2014-08-14
Actually yes, this is causing a problem.  The software updater is giving me a "Not all updates can be installed" message.  When I select "continue" it states "Software index is broken" and suggests I run "sudo apt-get install -f".  I have not run this command yet.  In synaptic, it doesn't show any broken packages, but the package that failed to be removed (syslinux-themes-debian) is marked for removal even after closing and reopening synaptic.

---

### Post by sudodus on 2014-08-14
Yes run 
```

sudo apt-get install -f
```

This list of useful commands was originally posted by *oldfred*

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

### Post by kev9982 on 2014-08-14
Thanks for your help.  I just wanted to make sure I wouldn't harm anything by running "sudo apt-get -f install".  This has allowed me to update my packages.

---

### Post by sudodus on 2014-08-14
I'm glad it worked for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

