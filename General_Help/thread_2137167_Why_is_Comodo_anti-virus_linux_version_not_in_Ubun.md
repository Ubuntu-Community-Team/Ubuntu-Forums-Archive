---
title: "Why is Comodo anti-virus linux version not in Ubuntu software center?"
date: 2013-04-19
forum: General Help
---

### Post by josephwcarrillo on 2013-04-19
The debain package "cav-linux_1.1.268025-1_i386.deb" can be downlowded from the Comodo anti-virus website [http://antivirus.comodo.com/](http://antivirus.comodo.com/) . The package can be opened with Ubuntu software center but can not be searched for using it. It also can not be uninstalled using the Ubuntu software center. To uninstall programs not in the Ubuntu software center you must use the command line such as sudo apt-get --purge remove package. There are also other great programs not found in the Ubuntu software center such as the Amaya web design tool. What is the reason that these programs can not be searched for in the Ubuntu software center?

---

### Post by deadflowr on 2013-04-19
Programs have to be in the various Ubuntu repositories for you to be able to find them in the software center.
If they are not in the repos, then they will not be listed in the software center.

Why they are not in the repos is another topic.

---

### Post by fantab on 2013-04-20
Ubuntu has a [Free Software Plilosophy]("http://www.ubuntu.com/about/about-ubuntu/our-philosophy"). Only the software that meets this criteria is provided through [Ubuntu Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu"). Regarding your particular software, Comodo Antivirus, Comodo must maintain a [ppa at Launchpad]("https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA") to 'distribute' its application through 'Ubuntu Software Center', which lists only the sofware that is available through ubuntu repositories. Basically the onus is not on Ubuntu but the application packager. 

I hope that was simple enough. :)

---

### Post by 3rdalbum on 2013-04-20
Nobody has time to find every single program on the internet and make them all available in the Ubuntu repositories. Some closed-source programs have licenses that prevent redistribution, too.

If you want to install these programs using Software Center, you can look for a repository or a PPA for them. When you add the PPA/repository to your system, Ubuntu Software Center will be able to recognise and install those programs, and Update Manager will be able to update them.

If no repository or PPA exists, you could ask the software developer to make a repository.

As you're new here, I'll also remind you that there are currently no viruses for Linux. The only reason you might want Comodo anti-virus is to scan for Windows viruses.

---

