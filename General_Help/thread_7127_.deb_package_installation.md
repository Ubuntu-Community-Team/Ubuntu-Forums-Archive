---
title: ".deb package installation"
date: 2004-12-04
forum: General Help
---

### Post by eduncan01 on 2004-12-04
Hi,

I am new to ubuntu. How do I install a .deb package from the folder I downloaded the .deb file to?

Thanks
Eric

---

### Post by ubuntu_demon on 2004-12-04
apt-get install packagename.deb

you might need root privileges then :

sudo apt-get install packagename.deb

---

### Post by jazzorist on 2004-12-05
sudo dpkg -i packagename.deb  
This only installs the chosen package. If there are dependencies, you'll have to apt-get them...

---

### Post by TravisNewman on 2004-12-05
Can a mod with power here move this to the proper location

---

### Post by jobezone on 2004-12-05
To install any package, you should probably first try to use apt-get, which automatically downloads it from the internet, along with any other package needed. It is the easiest way to install programs.

So, to install abiword, the word processor, you would do:
sudo apt-get install abiword

Or you could use Synaptic Package Manager, available in the menu Computer, where, after entering your password as asked, you would search first for abiword, then mark it for installation, then click the apply button.

If the package/app you want to install isn't available, that means it isn't available in the main repository. But ubuntu also hosts a Universe (and a Multiverse) repository which contain many more packages, the diference is they are not directly suported by ubuntu. You can turn these on using Synaptic inside the Repositories menu item. You should find more information on how to do this on ubuntu's ofical documentation at [http://www.ubuntulinux.org/support/documentation/helpcenter_view](http://www.ubuntulinux.org/support/documentation/helpcenter_view) and ubuntu's wiki at [http://www.ubuntulinux.org/wiki/](http://www.ubuntulinux.org/wiki/) .

If you really want to directly install .deb packages, do:

sudo dpkg -i <package>.deb

If all the dependencies this package needs are met, it will be installed. If not, those unfulfilled dependencies will me mentioned. You must now install this missing packages before installing the package you want, using any of the above methods (manually downloading the .deb files or automatically using apt-get or synaptic).

---

