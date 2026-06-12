---
title: "[SOLVED] mod_perl won't install"
date: 2007-07-25
forum: General Help
---

### Post by cancaseiro on 2007-07-25
Hi, tried to install mod_perl but in the end it gave me error: ```
[  error] Unable to open /usr/sbin/ap_release.h: No such file or directory
[  error] Unable to determine server version, aborting.
[  error] Please specify MP_APXS or MP_AP_PREFIX.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  PGOLLUCCI/mod_perl-2.0.3.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Failed during this command:
 PGOLLUCCI/mod_perl-2.0.3.tar.gz              : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256
```

Apache directory in Ubuntu Feisty should be /usr/sbin/, which I gave after it asked  ```
Please provide the location of the Apache directory:
``` but then why it had those errors, I am clueless now, can someone help? :confused:

---

### Post by cancaseiro on 2007-08-02
```
sudo apt-get install libapache2-mod-perl2
```

---

