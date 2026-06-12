---
title: "Dependencies =("
date: 2007-02-18
forum: General Help
---

### Post by Chake99 on 2007-02-18
I'm currently using Dapper Drake Kubuntu and I recently downloaded kamefu, tasty menu, katapult, and the .deb package for amarokFS.

Kamefu and tasty menu won't compile, failing numerous checks and then saying I need a version of Qt between 3.2 and 4.0, amarokfs installed but won't run, compaining about GLIBC_2.4, and katapult was the only program to work. 

There is no single Qt package or Qt dev package I could find in adept. "Qt3" returned many results, some of which I installed to no avail.

I tried to get glibc_2.4 but the closest things adept game me were libg++2.8.1.3-glibc2.2 and libstdc++2.10glibc2.2. 

Gah, what do I do? Is this because these packages are all edgy and I wasn't brave enough to upgrade? Must I hazard the fabled sudo apt-get dist-upgrade? Or am I simply missing a lot of packages?

And if so is there anyway to make synaptic/adept automatically fetch the packages that a tarball's compiling requires?

Thanks in Advance.

---

### Post by Chake99 on 2007-02-19
*bump*

---

### Post by mgmiller on 2007-02-19
If you are using the Dapper version, and you try to install something compiled for Edgy, it may (probably will) have dependencies for libraries that are not in Dapper.  If the apps you want are written only for Edgy, and you really really want to use them, then consider upgrading to Edgy.  It's not that bad as long as you mostly stayed with "normal" ubuntu repos.  The most important are where you got your video driver and kernel from.  I have upgraded 1 system I have from 5.04 to 5.10 to 6.04 to 6.10 with minimal problems.  If you do decide to upgrade, follow the methods given here on the forums for how to upgrade.  You don't have to manually configure anything.  It can almost totally be done from gui after 1 small entry at the command line.  It's all handled by update manager.

---

### Post by Chake99 on 2007-02-19
normal kernel, binary nvidia video driver, and xgl beryl installed (though I log into normal kde sessions).

Should I get rid of the latter two?

---

