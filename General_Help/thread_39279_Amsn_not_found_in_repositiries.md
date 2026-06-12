---
title: "Amsn not found in repositiries"
date: 2005-06-04
forum: General Help
---

### Post by still on 2005-06-04
hi all, this s my 1st post as ucan see :)

actually icant find the Amsn package either in synaptic or using the apt-get
i enabled the extra repositires in sources.list and added a few more mirrors too..
  tried to install it from the .deb file with no luck.
so whenever i try ( sudo apt-get install amsn) command i get the following:

still@master:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree... Done
Package amsn is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amsn has no installation candidate

so what can be done??
thanks all..

---

### Post by Gandalf on 2005-06-04
Amsn can be found in [universe](http://packages.ubuntu.com/hoary/x11/amsn)
take a look to [this](http://www.ubuntuguide.org)

---

### Post by still on 2005-06-04
its obvious that not all extra repositiries was enabled so icouldnt be able to find anything actually (ie. kedit, kget, amsn...etc)..
so that ubuntuguide "sources.list" did the job well!!
 
thanks alot  :)

---

