---
title: "location of c-header files for vmware"
date: 2006-07-14
forum: General Help
---

### Post by kinematic on 2006-07-14
Hey guys....i'm trying to install VMware-server so i d'loaded the Linux header files 2.6.15-26.44.
I didn't install the 2.6.16-26.44-686 headers for my AMD Sempron so that may be wrong.
Next i cdeed to the directory where i unpacked the VMware tarball and issued the command "./vmware-install.pl" and VMware installed.
Next I had to run vmware-config.pl wich asks for the c-header files but the kernel headers weren't located by the program(by default it looks in /usr/src/linux/include)
Should i have installed the 2.6.15-26.44-686 headers or can you guys tell me where to find the c-headers i have installed.

tia.

---

### Post by mazirian on 2006-07-14
There is a package for the kernel headers.  Installing it with apt will create the enecessary symlimnks to make things work for you.  At least, this is so under Debian proper.  Just be sure to install the kernel header package that corresponds to the kernel you are running.  I think that will help.

---

### Post by kinematic on 2006-07-14
installing the 2.6.16-26-686 headers did the trick.
i ran vmware-config.pl to configure vmware but i'm not able to run it because every time i try to run it be opening a terminal and typing "vmware" it says to run vmware-config.pl to properly (re)configure it for my system.
has anyone running vmware-server succesfully on ubuntu?

---

