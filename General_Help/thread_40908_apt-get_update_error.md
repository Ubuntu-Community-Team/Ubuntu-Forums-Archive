---
title: "apt-get update error"
date: 2005-06-11
forum: General Help
---

### Post by arunsub on 2005-06-11
I'm getting the following error while running apt-get update
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
  401 Authorization Required
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
  401 Authorization Required
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
  401 Authorization Required
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
  401 Authorization Required
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
  401 Authorization Required
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
  401 Authorization Required
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
  401 Authorization Required
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  401 Authorization Required
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz)  401 Authorization Required
Reading package lists... Done
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

This is my sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#deb [http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu](http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu) warty-updates main universe
#deb-src [http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu](http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu) warty-updates main universe 

What's the reason? Are backport sites down?

---

### Post by Kyral on 2005-06-11
You aren't supposed to use those Repos. Check the Backports Forums for the ones you are supposed to use

---

### Post by arunsub on 2005-06-13
Thanks. I changed them.

---

