---
title: "Update Manager - Cannot initialize package info"
date: 2013-01-07
forum: General Help
---

### Post by rbscairns on 2013-01-07
Ubuntu 12.04. I have bben trying to install GIMP 2.8.2 (still unsuccessful) but now have a problem.

When I try to open Update Madager, I get the following notification:
> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list'
I then go to /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list and open the file in text editor. It reads:
> deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main
deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main
ain
How do I solve this problem so as to get my Update Manager to properly open?

---

### Post by rbscairns on 2013-01-07
I'm getting better.

I used gedit to open /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list

I then deleted the offending "ain", saved and closed. Now Update Manager is working again.

---

