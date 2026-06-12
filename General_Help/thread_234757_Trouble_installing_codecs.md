---
title: "Trouble installing codecs"
date: 2006-08-12
forum: General Help
---

### Post by ajd344 on 2006-08-12
I researched for ever and figure this out!
When I go to install the extra codecs, it does this:

andrew@xion:~$ sudo aptitude install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libxine-extracodecs
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1176kB of archives. After unpacking 3047kB will be used.
The following packages have unmet dependencies:
  libxine-extracodecs: Depends: libmad0 (>= 0.15.1b) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.


Any help would be great! Thanks!

---

