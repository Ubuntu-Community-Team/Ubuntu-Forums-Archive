---
title: "Can't Install OpenOffice Ubuntu 16.04"
date: 2016-04-22
forum: General Help
---

### Post by techguy378 on 2016-04-22
I have a Dell C1760nw printer (Xerox Phaser 6000). When I use LibreOffice Writer I can't print envelopes. The screen showing the paper type options has everything grayed out and is stuck on letter size 8.5x11 paper. When I replace LibreOffice with OpenOffice on Ubuntu 16.04 it breaks the package system. The instructions below worked in Ubuntu 15.10, but in Ubuntu 16.04 LibreOffice seems to be a required part of the OS. After performing the instructions below I can't even install updates in Ubuntu 16.04 because I get a message that the package system is broken. Issuing "sudo apt-get -f install" in a Terminal window attempts to reinstall LibreOffice which fails since OpenOffice is installed. How do I fix this? Is Canonical trying to force LibreOffice down people's throats now?

Installing OpenOffice in Ubuntu 15.10:

```
sudo apt-get install openjdk-8-jre
sudo apt-get remove libreoffice* openoffice*
sudo apt-get autoremove
```

Then reboot.

After reboot:

```
sudo tar -xvf Apache_OpenOffice_4.1.2_Linux_x86_install-deb_en-US.tar.gz
sudo dpkg -i en-US/DEBS/*.deb en-US/DEBS/desktop-integration/openoffice4.1-debian-*.deb
```

---

