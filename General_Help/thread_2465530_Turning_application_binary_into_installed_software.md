---
title: "Turning application binary into installed software"
date: 2021-08-04
forum: General Help
---

### Post by jubale1328 on 2021-08-04
I have downloaded application binary for Second Life. I would like to turn that into a proper installed software, but I'm not sure how to do that. Must I convert it to a Ubuntu Package?

---

### Post by grahammechanical on 2021-08-04
It is my understanding, and I may be wrong, but binary files need to be packaged by a package manager. What is the file extension of the binary file? Ubuntu is based on Debian and so we can install applications that have been packaged in the Debian package format. Such files will have a .deb file name extension.

I am also aware of the Redhat Package Manager format. Those application packages have a .rpm file name extension and cannot be installed on Ubuntu. There are a few other package formats that are designed to be Linux distribution independent. I do not think that those package formats are relevant to your question. Ubuntu users need to do very little to make it possible to install applications in those package formats.

Regards

---

### Post by dragonfly41 on 2021-08-04
From a brief reading I understand that Second Life is some form of avatar game.
You could package custom app in [Electron wrapper]("https://www.electronjs.org/").
You would need to run a subprocess.

---

### Post by TheFu on 2021-08-04
There is no such thing as an "Ubuntu Package". 

There isn't just 1 method to create an installer and there isn't just 1 type of installer.  Installers can be a little shell script, a compiled program (that does what the shell script does), a makefile that copies stuff to specific places (like the shell script does), a snap package, a flatpack package, an AppImage package, a debian package, or some other installation type based on the language used.  So, perl, python, ruby, and java all have their own package management systems.  It is possible to use those for other languages too, but that is seldom done.

So ... there are lots of ways.

If you want the package to be fully integrated into APT on Ubuntu, then you must use the .deb file format. I always found this to be too much hassle and usually go with either a makefile or a shell script for packaging.  I find these to be easier for me to understand and they work just as well, assuming there aren't many outside dependencies. They are also easy to provide for all Linux installations, not just ubuntu.  

OTOH, if the program has lots of dependencies and dependency management from the system package system (APT) is require for your sanity, then only a .deb package can really fulfill that need. [https://wiki.debian.org/HowToPackageForDebian](https://wiki.debian.org/HowToPackageForDebian)  is how I'd begin.

If you aren't a programmer and don't full understand dependencies, I suspect getting in over your head is likely.

---

### Post by deadflowr on 2021-08-04
A binary for all in tents and porpoises is usually already software. Most likely ready to go, with perhaps a simple tick of a box to mark as executable.
What you probably want is to create a desktop launcher for ease of use.
See: [https://www.maketecheasier.com/create-desktop-file-linux/]("https://www.maketecheasier.com/create-desktop-file-linux/")
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")
For general concepts about creating launchers.

Beside that we haven't any idea what binary it is or from where so any additional information about it will help.

I do see [secondlife's support page]("https://secondlife.com/system-requirements") states it requires 32-bit compatibility, which may not be complete on Ubuntu 20.04,
as Ubuntu just prior to 20.04 dropped full 32-bit support and only has a limited number of 32-bit based packages.
So it is unclear whether or not Ubuntu can even run it.

---

