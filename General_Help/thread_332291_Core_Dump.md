---
title: "Core Dump?"
date: 2007-01-05
forum: General Help
---

### Post by Ripfox on 2007-01-05
What can I do about this?

I tried to install some stuff through synaptic, then uninstalled it (JACKd and ardour ect...)
now I get:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Segmentation fault (core dumped)
Setting up cmt (1.15-3.1) ...
Segmentation fault (core dumped)
dpkg: error processing cmt (--configure):
subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
cmt
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks all :D

---

### Post by Ripfox on 2007-01-07
Fixed it...just kept uninstalling stuff then did a -f install again and it cleared up. Sorry to wast any time :(

---

