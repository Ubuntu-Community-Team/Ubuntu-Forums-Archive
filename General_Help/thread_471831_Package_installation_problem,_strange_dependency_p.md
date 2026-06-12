---
title: "Package installation problem, strange dependency problem"
date: 2007-06-12
forum: General Help
---

### Post by 7llusion on 2007-06-12
I've been triyng to install my Canon Pixma IP1500, but I get this strange problem when trying to install a required package:
```
grubb@grubb-laptop:~$ sudo apt-get install pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pstocanonbj: Depends: libcupsys2-gnutls10 (>= 1.1.23-1)
E: Broken packages
grubb@grubb-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
But when I try this:
```
grubb@grubb-laptop:~$ sudo apt-get install libcupsys2-gnutls10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcupsys2 instead of libcupsys2-gnutls10
libcupsys2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Nothing works...
Please help
Illusion

---

### Post by az on 2007-06-12
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libcupsys2-gnutls10+&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libcupsys2-gnutls10+&searchon=names&subword=1&version=all&release=all)

What version of Ubuntu are you running?

---

### Post by 7llusion on 2007-06-13
I'm using Feisty, with all the available updates.

---

### Post by dryder on 2007-06-16
I have the same problem with Canon's debian driver for the LBP300.

Would it be better to compile using the source code?

David

---

