---
title: "Clean Uninstall of MySQL"
date: 2007-12-25
forum: General Help
---

### Post by sharpycore on 2007-12-25
Hi,
I have been trying to install MySQL at the command line from a package downloaded from the website (before I realised I could just do apt-get etc...) and I've made a mess of it. Some of the commands are recognised but just throw up error messages (e.g. mysqld is recognised by  ubuntu but doesn't run properly, complains about permissions) but the install doesn't show up in any of the package managers and sudo apt-get remove mysql fails with "E: Couldn't find package mysqld."

What's the best way to cleanly remove all the mess I've made so I can try again from scratch? I'm guessing just deleting all the installation directories is going to make a total mess. Is there a more careful way to go about it?

Thanks,
Tom

---

### Post by TidusBlade on 2007-12-25
Maybe just "apt-get purge <package name>" which also removed configuration files.

---

