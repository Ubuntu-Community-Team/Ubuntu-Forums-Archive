---
title: "Software integration and install locations?"
date: 2016-02-19
forum: General Help
---

### Post by peter1897 on 2016-02-19
How the installed applications in Ubuntu are integrating with the system in comparison with the applications in Windows OS? In Windows the integration is through the registry where the default programs for each file extension are set. Also in the registry you can control what is appearing in right click context menu.

Is there a program for Ubuntu, that can work in similar way as Regshot for Windows, and monitor the installation process of a program - what are the locations where the program installs files and what changes it makes to the system?
Or program similar to Process Monitor from Sysinternals?

---

### Post by oldos2er on 2016-02-19
File extensions are fairly meaningless on Linux, instead it uses file types, also called MIME types. Where file extensions exist, they are for the benefit of the human being, less so for the operating system. There is no registry that functions like the one in Windows.

Linux uses a package manager to monitor the installation, placement, and removal of software. There's information on Ubuntu's package manager at these links:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

