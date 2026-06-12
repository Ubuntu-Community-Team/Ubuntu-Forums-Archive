---
title: "[SOLVED] Bugzilla fails to install"
date: 2008-01-20
forum: General Help
---

### Post by cewan on 2008-01-20
When trying to install bugzilla by writing:
```
sudo aptitude install bugzilla
```
I get the following error:
```

Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bugzilla (2.22.1-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/dbconfig-common/bugzilla.conf
unable to read input file /etc/dbconfig-common/bugzilla.conf
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bugzilla

```

What can I do to fix this?

---

### Post by cewan on 2008-01-21
Maybe I should post the entire output:

```

$ sudo aptitude install bugzilla
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up bugzilla (2.22.1-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/dbconfig-common/bugzilla.conf
unable to read input file /etc/dbconfig-common/bugzilla.conf
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bugzilla (2.22.1-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/dbconfig-common/bugzilla.conf
unable to read input file /etc/dbconfig-common/bugzilla.conf
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bugzilla

```

Anyone that has any idea on how to fix this?

---

### Post by cewan on 2008-01-22
[http://www.linuxquestions.org/questions/linux-software-2/problems-installing-bugzilla-615430/](http://www.linuxquestions.org/questions/linux-software-2/problems-installing-bugzilla-615430/)

---

