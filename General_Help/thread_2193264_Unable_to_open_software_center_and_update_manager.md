---
title: "Unable to open software center and update manager"
date: 2013-12-12
forum: General Help
---

### Post by supin89 on 2013-12-12
Hi,
I am a new Linux user and I am using Ubuntu 12.04
I am getting the following error message while opening update managr

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/glug.nith.ac.in_ubuntu_archives_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'"


Also I am unable to open software center. Whenever I try to open it is closing unexpectedly


Pls help
Thankyou

---

### Post by plucky on 2013-12-12
> "Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Problem with MergeList /var/lib/apt/lists/glug.nith.ac.in_ubuntu_archives_dists_precise_main _binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'"


Open a terminal and run ```
sudo rm -rf /var/lib/apt/lists/*
``` and then run ```
sudo apt-get update
``` and see if the error still occurs.

Good Luck

---

