---
title: "dpkg: serious warning"
date: 2006-07-11
forum: General Help
---

### Post by _simon_ on 2006-07-11
I just used apt-get to get xbindkeys and this displayed in terminal at the bottom:

dpkg: serious warning: files list file for package `xserver-xorg-driver-vmware' missing, assuming package has no files currently installed.

I've tried re-installing `xserver-xorg-driver-vmware' but it seems to have made no difference. How do i fix this?

---

### Post by NESFreak on 2006-07-11
if you DO have it already installed it, the version you intstalled is probalby an older version. Try udating it manualy, or try deleting the dependency from the .dep file your installing. Both methods may result in a crashing system.

removing the dependency form the package:

cd /where/the/package/is
mkdir xbindkeys
dpkg-deb --extract <the package>.deb 
dpkg-deb --control <the package>.deb xbindkeys
gedit xbindkeys/DEBIAN/control

Remove the "xserver-xorg-driver-vmware X.X.X part" from the depends list. Save and exit.

dpkg --build xbindkeys
sudo dpkg -i xbindkeys.deb

---

