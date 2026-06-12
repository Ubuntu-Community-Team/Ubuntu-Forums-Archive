---
title: "Help with Google Earth"
date: 2007-06-06
forum: General Help
---

### Post by jingdejun on 2007-06-06
I tried to install Google earth under Ubuntu Feisty on my AMD-64 desktop, got following error:
--------
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.1.7076.4458..........................................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
-------------

Do I need to install something for my linux? I searched in 'Add/Remove...' and Synaptic package manager, can not find 'gtk2'.

---

### Post by JAPrufrock on 2007-06-07
You should have gtk2 in the repositories.  In my synaptic gtk2 is in the main repository (us.archive.ubuntu.com/main).

---

### Post by mcduck on 2007-06-07
You already have GTK2. All Gnome programs use GTK2 :D

Anyway, Your problem is probably that you are trying to install 32-bit version of Google Earth while running 64-bit Ubuntu.

I recommend using Medibuntu repository, it has both 32-bit and 64-bit versions of Google Earth, and installing it through package management makes updating and removing it easier than if you use their own binary installer.

[http://medibuntu.sos-sts.com/index.php]("http://medibuntu.sos-sts.com/index.php")

---

### Post by darkteckno on 2007-06-07
not the latest version though

---

