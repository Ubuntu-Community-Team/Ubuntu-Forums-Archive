---
title: "Repositories and self-compiled softwares"
date: 2007-11-11
forum: General Help
---

### Post by flip79 on 2007-11-11
Hello, I've a doubt: if I install something on my system, and repositories in my sources.list contain the same software in a previous version... will I get a notify when the software will be available in repositories, in a more recent version than the one I installed? Or when I self-compile a program it is no more associated to the distro?

---

### Post by justin_guerin on 2007-11-11
When a version installed is newer than the most recent version available in the repository, the package manager will not install the version from the repository.  However, when the version in the repository goes higher than the version you have installed, then the package manager will prompt you to upgrade that package.

With self compiled programs, it can go either way.  If you compiled into a package and used the package manager to install it, then the package manager will also know when a newer version appears in the repository, and will prompt you to upgrade when that happens.  However, if you've simply compiled the application binaries and copied them to their destination folders, but did not create a package, then the package manager doesn't know the program is installed, and won't prompt you when a newer version is available.

Hope that helps,
Justin

---

### Post by flip79 on 2007-11-12
Thank you very much Justin!
So, does "make install" tracks future updates? And what about "dpkg -i"?

---

### Post by mcduck on 2007-11-12
No, that won't work. If you just compile a program it's not registered by the package management in any way, and therefore you won't get automatic updates.

But there is a way to get it working. Just install the 'checkinstall' package, and then when compiling a program instead of running 'sudo make install' you run 'sudo checkinstall'. Checkinstall will create a .deb package from your compiled program, and then install it through the package manager.

Installing .deb packages with 'sudo dpkg -i' will of course register them in the package management. Actually that's exactly what apt-get, Synaptic and other package management tools do to install the packages.

---

### Post by flip79 on 2007-11-12
Ok, now it's clear. Thank you!!!

---

