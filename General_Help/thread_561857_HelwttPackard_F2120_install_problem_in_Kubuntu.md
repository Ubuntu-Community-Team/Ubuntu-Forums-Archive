---
title: "HelwttPackard F2120 install problem in Kubuntu"
date: 2007-09-28
forum: General Help
---

### Post by tonymoloney on 2007-09-28
I have just purchased a HP F2120 printer and when I follow the installation guide I get to a point where it tells me the following dependencies are missing:
gcc, libpthread, cups-devel, libusb, libtool, libjpeg, sane-devel, pil, scanimage, xsane
It then asks if I want to install the missing files and checks for a network connection.
Even though I am on ADSL, it says it can't make the connection and the process aborts.
I have downloaded gcc but don't really know where to put it.
My attempts to find libpthread have frustrated me, which is why I am asking for help.
Has anyone any insight into this problem, please?

---

### Post by tonymoloney on 2007-09-28
bump

---

### Post by tonymoloney on 2007-09-29
Bump, again

---

### Post by Maestro23 on 2007-09-29
You should be able to find those dependencies via Synaptic.  Open up Synaptic, search for each one, and install.  Then try and setup your printer again.

Make sure all your repo's are enabled. (Universe, Multiverse)

[https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29](https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29)

---

