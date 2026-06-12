---
title: "gimpshop takeover"
date: 2007-09-20
forum: General Help
---

### Post by thematthewknot1 on 2007-09-20
i recentyl installed gimp shop on ubuntu 7.04 from this link [http://rapidshare.com/files/23828509/gimpshop_2.2.11-1_i386.deb](http://rapidshare.com/files/23828509/gimpshop_2.2.11-1_i386.deb) but something has gone wrong with it when installing now every time i start linux i have the update manager saying this
[IMG]http://3too1.com/pic/images/Screenshot-update-manager.png[/IMG]
 and when ever i try to start the package manager i get this 
[IMG]http://3too1.com/pic/images/Screenshot-synaptic.png[/IMG]
 how do i either uninstall this or install it fully? please help:frown:

---

### Post by Maestro23 on 2007-09-20
Try this on the package you installed:

> sudo dpkg --force-remove-reinstreq –remove pkgname

---

