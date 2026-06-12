---
title: "mdadm missing in ubuntu 7.10?"
date: 2008-01-09
forum: General Help
---

### Post by kochakaden on 2008-01-09
I've just done a fresh install of ubuntu 7.10 on my machine, and mdadm is not installed on it, nor can it be installed:

root@files:/sbin# mdadm
The program 'mdadm' is currently not installed.  You can install it by typing:
apt-get install mdadm
bash: mdadm: command not found
root@files:/sbin# apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mdadm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mdadm has no installation candidate
root@files:/sbin#

---

