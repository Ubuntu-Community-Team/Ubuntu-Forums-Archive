---
title: "Can't install Amarok"
date: 2006-12-28
forum: General Help
---

### Post by chrispche on 2006-12-28
Please help I tried to install amarok thus:

chrispche@chrispche-desktop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  amarok-xine
Suggested packages:
  libvisual-0.4-plugins konqueror www-browser libqt0-ruby1.8 amarok-engines
Recommended packages:
  kdemultimedia-kio-plugins
The following NEW packages will be installed:
  amarok amarok-xine
0 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
Need to get 17.1MB/17.2MB of archives.
After unpacking 32.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  amarok-xine amarok
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main amarok 2:1.4.3-0ubuntu8~dapper1
  Bad header line [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.3-0ubuntu8~dapper1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.3-0ubuntu8~dapper1_i386.deb)  Bad header line [IP: 195.248.90.35 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chrispche@chrispche-desktop:~$

Thats the error message I got.

---

### Post by pay on 2006-12-28
Have you tried what it says? "maybe run apt-get update or try with --fix-missing"```
sudo apt-get update
sudo apt-get amarok --fix-missing
```

---

### Post by chrispche on 2006-12-29
Ok I done as you advised and got:

chrispche@chrispche-desktop:~$ sudo apt-get install amarok --fix-missing
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  amarok-xine
Suggested packages:
  libvisual-0.4-plugins konqueror www-browser libqt0-ruby1.8 amarok-engines
Recommended packages:
  kdemultimedia-kio-plugins
The following NEW packages will be installed:
  amarok amarok-xine
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.1MB/17.2MB of archives.
After unpacking 32.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main amarok 2:1.4.3-0ubuntu8~dapper1
  Bad header line [IP: 195.248.90.38 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.3-0ubuntu8~dapper1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.3-0ubuntu8~dapper1_i386.deb)  Bad header line [IP: 195.248.90.38 80]
chrispche@chrispche-desktop:~$

Same error message.

---

