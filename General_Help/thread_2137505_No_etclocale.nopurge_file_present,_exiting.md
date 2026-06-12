---
title: "No /etc/locale.nopurge file present, exiting"
date: 2013-04-21
forum: General Help
---

### Post by modest intentions on 2013-04-21
I was playing around with Localepurge trying to install it than i ran into this little error everytime i " apt-get upgrade", i cant seem to find a fix anywhere that helps me get my" /locale.nopurge file" back :O

Do you want to continue [Y/n]? y
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 82, <$__ANONIO__> chunk 1.
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.6.1-2ubuntu1) ...
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 82, <$__ANONIO__> chunk 1.
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up localepurge (0.6.2+nmu2) ...
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 82, <$__ANONIO__> chunk 1.
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing localepurge (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 localepurge
 No /etc/locale.nopurge file present, exiting ...
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

