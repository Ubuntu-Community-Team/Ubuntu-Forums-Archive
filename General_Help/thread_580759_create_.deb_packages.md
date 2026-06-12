---
title: "create .deb packages"
date: 2007-10-19
forum: General Help
---

### Post by gayathri on 2007-10-19
Hi, 

                  I am here to know abt how to create a .deb pkg without using checkinstall and deploy it.

---

### Post by jocko on 2007-10-19
A few guides to get you started:

[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-scratch.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-scratch.html)
[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

Those links should explain how to "debianize" the build process in order to build real .deb packages.
Note that some program sources (and probably all you can get through synaptic?) are already "debianized", and can be used to build proper debian packages as they are (check if the source you want to build from already contains a debian/ directory).

Good luck!

---

