---
title: "Cannot install flightgear"
date: 2005-09-17
forum: General Help
---

### Post by arlie on 2005-09-17
arlie@jackal:~$ sudo dpkg -i flightgear_0.9.8-3_i386.deb
Password:
Selecting previously deselected package flightgear.
(Reading database ... 90707 files and directories currently installed.)
Unpacking flightgear (from flightgear_0.9.8-3_i386.deb) ...
dpkg: dependency problems prevent configuration of flightgear:
 flightgear depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 flightgear depends on libgcc1 (>= 1:4.0.0-9); however:
  Version of libgcc1 on system is 1:4.0.0-7ubuntu6~5.04ubp1.
 flightgear depends on libstdc++6 (>= 4.0.1); however:
  Package libstdc++6 is not installed.
 flightgear depends on plib1.8.4c2; however:
  Package plib1.8.4c2 is not installed.
 flightgear depends on simgear0 (>= 0.3.8-2); however:
  Package simgear0 is not installed.
 flightgear depends on fgfs-base (>= 0.9.8); however:
  Package fgfs-base is not installed.
dpkg: error processing flightgear (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flightgear
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

What files do I need to install and where can I get it?

---

### Post by rusi_pathan on 2005-09-17
Ubuntu does not have the version 0.9.8. You should give v0.9.5 a try. It can be installed using...

$ sudo apt-get install flightgear


or else compile from source.

---

