---
title: "Config of bacula"
date: 2007-12-02
forum: General Help
---

### Post by Harlyman on 2007-12-02
hello

need some help on installing bacula on my ubuntu system with mysql support with apt-get, this fails because it try to install the db's on mysql without any password, and this is a production system with password set, any tips on how i can get dpkg to use passwd when it installs the bacula-director-mysql

---

### Post by dbtrade on 2008-06-20
use this link...

[http://wiki.bacula.org/doku.php?id=howto_compile_and_install_bacula_on_debian_4.0_etch](http://wiki.bacula.org/doku.php?id=howto_compile_and_install_bacula_on_debian_4.0_etch)

When you get to the part about configuring MySQL for bacula, add the -p switch to the end of each of the command line that calls each of the 3 scripts.

This will prompt you for your MySQL password.

It's the cleanest way.

---

