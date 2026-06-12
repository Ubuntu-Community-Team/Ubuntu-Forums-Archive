---
title: "[SOLVED] I need to do the following in terminal...."
date: 2007-07-02
forum: General Help
---

### Post by jawinterton on 2007-07-02
Help!  I need to know how to do the following in Ubuntu from the safe mode terminal (my system is broken w/ nvidia problems):

1- see which linux-headers package I have installed. ** Also, how do you find out which kernel you are running and how would one go about getting the correct matching headers installed from terminal if necessary?

2-install pkg-config and xserver-xorg-dev

3-uninstall the nvidia-glx package w/ the purge option.  

4-uninstall other things in general.

---

### Post by oldmanstan on 2007-07-02
1) restricted headers should be in /lib/linux-restricted-modules/ in a subfolder with the name of your kernel, to find your kernel do
```
uname -r
```
in a terminal or command line
to install new headers i think you can just use sudo apt-get install  linux-restricted-modules-2.6.20 (change to your kernel version

2) ```
sudo apt-get install pkg-config xserver-xorg-dev
```

3) ```
sudo aptitude purge nvidia-glx
```

4) ```
sudo apt-get remove <package>
``` or ```
sudo aptitude purge <package>
``` (this removes configuration files also)

---

