---
title: "i can't install the nvidia driver on edgy"
date: 2007-03-21
forum: General Help
---

### Post by kanpachi on 2007-03-21
hello i'm using edgy on an athlon xp 2800 with 512 ram and a 80 gb hd
i just installed edgy after using dapper for awhile
everything works great except one tiny problem
i can't install the nvidia driver in any way!
i have a nvidia geforce 4 mx, so i installed nvidia-glx-legacy and after that, x won't load for me
so i tried the envy script and it didn't work either!
and while running "sudo dpkg reconfigure xserver-xorg" i suddenly notice x won't detect my graphic card or monitor (samsung syncmaster 955df 19 CRT) like it did on dapper
it just says "generic"
any ideas please?

---

### Post by sdil on 2007-03-21
I think you must install Envy 3d card driver from : [http://albertomilone.com/](http://albertomilone.com/)

---

### Post by Xceptiona1 on 2007-03-21
I'm not certain if you want to try installing the binary drivers or not, but I am in the process of learning how to properly do that.

I found this in the Nvidia forums.
---------------
Debian GNU/Linux or Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.
If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv"
----------------------

I currently have it 'working' but upon reboot I am having issues, that will hopfully be fixed tonight. I think my issue is in the fact that I did not remove the nvidia-glx stuff yet.

---

### Post by profXavier on 2007-03-21
Ok, you want to read a bit about installing your Nvidia driver, one place to start would be the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy").  First off, you want to read the guide, its pretty straight forward in the driver install.

Now if you have any questions after this, then please visit #ubuntu-effects on IRC.freenode.org.  The people on that channel will help you alot.

profXavier

---

### Post by robroy911 on 2007-03-21
I am having this issue as well.  My system is a Athalon XP 2600, 1 GB DDR, Geforce Ti4800.
This happens with both 6.06 and 6.10.  Using envy, automatix, apt-get (and modifying the xorg.conf) legecy and current nvidia-glx drivers and attempted to build the driver downloaded from Nvidia's Website.  All those options failed.

I am still looking for an answer to this.  This reminds me of Debian Potato.  What a pain in the rear!

---

