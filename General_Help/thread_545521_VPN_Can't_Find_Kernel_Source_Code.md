---
title: "VPN Can't Find Kernel Source Code"
date: 2007-09-07
forum: General Help
---

### Post by likegiraffes on 2007-09-07
I have been working with this for hours now, and its driving me nuts.  I finally managed to get the VPN Client installed (its a specific client for my university, which I have to use).  However, I can't get it to work because it can't find the source code.  I installed the Linux 2.6.20 source/headers but I don't know where they are?  I'm so confused.  Here's what the terminal is saying:

mfarrell@dell:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]y

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.20-16-generic/build]/usr/src/linux-headers-2.6.20-16-generic

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.20-16-generic" will be used to build the module.

Is the above correct [y]y

Making module
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/mfarrell/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/mfarrell/vpnclient/linuxcniapi.o
/home/mfarrell/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/mfarrell/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/mfarrell/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
Copying module to directory "/lib/modules/2.6.20-16-generic/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.
Creating global config /etc/opt/cisco-vpnclient

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* New Profiles     : offcampus oncampus sample ub ubVPN 

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
    /opt/cisco-vpnclient/bin/ipseclog
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.
mfarrell@dell:~/vpnclient$ /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: Failed (super user access required)
mfarrell@dell:~/vpnclient$ sudo /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.20-16-generic/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)
mfarrell@dell:~/vpnclient$ 


I really need to figure this out soon so I can do my programming homework this weekend.  Any help at all would be hugely appreciated!

---

### Post by likegiraffes on 2007-09-07
I know that's kind of a lot, but I'm pretty sure the problem just has to do with my answer to:

Directory containing linux kernel source code [/lib/modules/2.6.20-16-generic/build]

I don't know what to type there.

---

### Post by bettlebrox on 2007-09-07
Do you have the kernel headers installed for your kernel?

---

### Post by likegiraffes on 2007-09-07
I'm pretty sure I do.  I downloaded a package.  I have four folders in the usr/src directory:

linux-headers-2.6.20-15
linux-headers-2.6.20-15-generic
linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic

---

### Post by bettlebrox on 2007-09-07
I remember building the Cisco VPN client a few years ago and it's a bit of bear to get to work. Plus, it may not work with later versions of the Linux kernel. I don't use it anymore as work now only allows people using MS windows to connect! :mad: U may want to google around to see if you can get the latest verison. Or see if anyone else has gotten it work with the version of kernel your using.

---

### Post by likegiraffes on 2007-09-07
Thanks for your help.  According to the documentation, the version I dowloaded should work with "other" versions of linux based on the 2.6 kernel.  That was my only option, pretty much.  I don't think I can use any other program to get into the Campus computer; security is pretty hardcore.

Do you have any idea what directory what it wants would be in?  I'm pretty sure that's where the problem is, but I don't really know.

---

