---
title: "System crash after trying to install Adobe Reader"
date: 2022-06-27
forum: General Help
---

### Post by Ralph L on 2022-06-27
Got the system crash message "Ubuntu 22.04 has experienced an internal error". The cause: "You have some obsolete package versions installed: libsystemd0, libudev1,udev.Using synaptic I could see that I have libsystemd0 ver 249.11-0ubuntu3.1 and libsystemd0:i386 ver 249.11-0ubuntu3.1 installed. ibsystemd0:i386 is for 32 bit. I recently enabled the 32 bit architecture with ```
$ sudo dpkg --add-architecture i386
$ sudo apt update
``` while trying to get adobe reader installed following the directions here: [https://linuxconfig.org/how-to-install-adobe-acrobat-reader-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-adobe-acrobat-reader-on-ubuntu-20-04-focal-fossa-linux) . Is adding a 32 bit architecture a no-no in jammy. The web site is for focal not jammy but I thought I would try it. I couldn't find a web site for installing Adobe reader in jammy. Is installing Adobe reader in jammy not possible????

---

### Post by cyberkingdom on 2022-06-27
You could try to use the Acrordrdc snap from the snap store [https://snapcraft.io/acrordrdc](https://snapcraft.io/acrordrdc).

---

