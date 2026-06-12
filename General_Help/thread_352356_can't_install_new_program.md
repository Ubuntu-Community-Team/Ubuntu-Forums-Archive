---
title: "can't install new program"
date: 2007-02-03
forum: General Help
---

### Post by Artiom on 2007-02-03
hi,

When I'm trying to install any new program or update it throws this error:

artiom@artiom-desktop:~$ sudo apt-get install php5-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5-cli php5-common
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/2444kB of archives.
After unpacking 5509kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing /var/cache/apt/archives/php5-common_5.1.6-1ubuntu2.1_i386.deb (--unpack):
 unable to open files list file for package `gnome-keyring': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/php5-common_5.1.6-1ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


any ideas what this might be?

---

### Post by tzulberti on 2007-02-03
Try: "sudo apt-get -f install" to solve the problem

---

### Post by Artiom on 2007-02-03
> **tzulberti said:**
> Try: "sudo apt-get -f install" to solve the problem

didn't help :(

---

### Post by Artiom on 2007-02-04
bump

---

