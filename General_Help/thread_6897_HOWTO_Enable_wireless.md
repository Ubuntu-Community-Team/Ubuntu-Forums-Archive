---
title: "HOWTO: Enable wireless"
date: 2004-12-02
forum: General Help
---

### Post by Infatuated_iPod on 2004-12-02
I have a Dell Inspiron 8600, and i need to get the wireles on it working, it says i need to edit /etc/apt/sources.list, when i get there i have absolutely no idea what to do... i need nsdiwrapper... someone help..

---

### Post by jdodson on 2004-12-02
install ndiswrapper from synaptic or you can install it from the console by typing:

```
sudo apt-get update
sudo apt-get install ndiswrapper
``` 

from there follow this installation guide(make sure to skip the part about installing ndiswrapper because it is already installed)

[http://ndiswrapper.sourceforge.net/wiki/index.php/Installation](http://ndiswrapper.sourceforge.net/wiki/index.php/Installation)

i was able to get ndiswrapper working by compiling ndiswrapper from source.

---

### Post by az on 2004-12-02
If you need more recont modules compiled for the Warty default kernel, install these two packages.


[http://www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb](http://www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb)
[http://www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb](http://www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb)

download them to a floppy and then do
sudo dpkg -i ndiswrapper*.deb

---

### Post by mr_ed on 2004-12-02
First of all, can you use your laptop to download packages?
If so, with respect to editing your /etc/apt/sources.list, you need to enable universe, so add "universe" on the end of "main" and "restricted" for all entries in that file (except the one on the CD).

Open up Synaptic and do an Update.
I believe the package is called ndiswrapper-utils.  Do a search for ndiswrapper and you'll find it.

After that is installed, download the Windows driver for your card, and save it somewhere like /home/user/driver.  Unzip it with file-roller or some extraction program.
Point your terminal to that folder, and type
sudo ndiswrapper -i [DRIVERFILENAME.INF] (make sure you have the case sensitivity right.  In my case it was all uppercase)
Now type
sudo modprobe ndiswrapper
You should now have a wlan device.

---

