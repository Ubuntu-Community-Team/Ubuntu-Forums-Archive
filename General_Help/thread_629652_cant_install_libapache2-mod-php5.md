---
title: "cant install libapache2-mod-php5"
date: 2007-12-02
forum: General Help
---

### Post by react9 on 2007-12-02
Hi,

I am trying to install libapache2-mod-php5 along with php5, but i keep getting the following error:

[I]
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.3-1ubuntu6.1_i386.deb) ...
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.1) ...
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN0> line 1.
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

This is a clean install i just did yesterday of 7.10, and i don't think i have installed anything else other than apache2.  

Any help is appreciated.

Thanks,

---

### Post by prendreuncafe on 2008-05-16
Run /usr/share/debconf/fix_db.pl as root user

---

