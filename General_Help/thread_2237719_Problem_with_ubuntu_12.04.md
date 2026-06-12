---
title: "Problem with ubuntu 12.04"
date: 2014-08-03
forum: General Help
---

### Post by ujwaladhikary2008 on 2014-08-03
I am currently using 12.04.Recently while updating totem player for playing H264 video some message are coming

1.Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

2.The error message is 'Error:opening the cache (E encountered a section with no package:header,E:Problem with Mergelist/var/lib/apt/lists/Security.ubuntu.com_ubuntu_dist_precise-security_restricted_binary-i386_packages

---

### Post by ajgreeny on 2014-08-03
Run command ```
sudo rm /var/lib/apt/lists/Security.ubuntu.com_ubuntu_dist_precise-security_restricted_binary-i386_package
``` and then run ```
sudo apt-get update
sudo apt-get upgrade
``` 						and try again.

---

