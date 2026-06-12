---
title: "install acroread"
date: 2005-03-22
forum: General Help
---

### Post by cd1680 on 2005-03-22
hi i am new to ubuntu and i am tryiing to install acroread
i type sudo apt-get install acroread and get this error message:
Reading Package Lists... Done
Building Dependency Tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  acroread-debian-files
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package acroread has no installation candidate

i have edited the repositories to include universe but somehow it doesnt work.
does anyone know the problem? thanks
btw i am running 4.10 on amd64

---

### Post by Leif on 2005-04-08
For one thing, the backports repository has changed, see [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/). Still having this problem ?

---

### Post by bored2k on 2005-04-08
[http://ubuntuguide.org/#acroread](http://ubuntuguide.org/#acroread)

---

