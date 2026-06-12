---
title: "Kernel patch"
date: 2013-12-07
forum: General Help
---

### Post by hgabor1989 on 2013-12-07
Hi All!


I would like to install a program on Ubuntu 12.10.
I have to patch the kernel and I follow the guide at the buttom of the page.
I made all of steps but something wrong.
I get this output when I run ./configure command:
[https://dl.dropboxusercontent.com/u/91011488/NG_makeall4.png](https://dl.dropboxusercontent.com/u/91011488/NG_makeall4.png)

netconf.h is not at the right place. I found it at:
/usr/scr/linux-3.8.2-mip6dng/include/uapi/linux/netconf.h


Wat could be the problem?


Where can I type the commands os the 4th step? In linux-stable/ directory?


Thanks!


1. Tools you'll need
--------------------
sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge kernel-package
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev


2. Getting the kernel source
-----------------------------
git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
git tag -l
git checkout


3. Patching
-----------
patch -p1 -d linux-stable -i /patches/kernel//*


4. Configuration
----------------
cp /boot/config-`uname -r` .config
yes '' | make oldconfig
make menuconfig
Networking support / Networking options
Transformation sub policy support ==> y/m
Networking support / Networking options / The IPv6 protocol
IPv6: Mobility ==> y/m
IPv6: XFRM raw IPv6 tunnel ==> y/m


5. Compiling kernel
-------------------
cd linux-stable
make clean
make -j `getconf _NPROCESSORS_ONLN` deb-pkg LOCALVERSION=-mip6dng


6. Installing the kernel
------------------------
sudo dpkg -i linux-image--*_i386.deb
sudo dpkg -i linux-headers--*_i386.deb

---

