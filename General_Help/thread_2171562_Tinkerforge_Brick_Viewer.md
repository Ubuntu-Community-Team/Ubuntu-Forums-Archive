---
title: "Tinkerforge Brick Viewer"
date: 2013-08-31
forum: General Help
---

### Post by Edward_Baker on 2013-08-31
I'm new to Raspberry Pi and am trying to install brick viewer software, however i keep getting errors see below - please helpi've rebooted so there were no other apps running at the time, entered LXTerminal and typed the following commands.pi@raspberrypi ~ $ sudo apt-get install python-twisted python-gudev libusb-1.0-0Reading package lists... DoneBuilding dependency tree       Reading state information... Donelibusb-1.0-0 is already the newest version.python-gudev is already the newest version.python-twisted is already the newest version.You might want to run 'apt-get -f install' to correct these:The following packages have unmet dependencies: brickv : Depends: python-qt4 but it is not going to be installed          Depends: python-qt4-gl but it is not going to be installed          Depends: python-qwt5-qt4 but it is not going to be installed          Depends: python-opengl but it is not going to be installedE: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).pi@raspberrypi ~ $ apt-get -f installE: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?pi@raspberrypi ~ $

---

