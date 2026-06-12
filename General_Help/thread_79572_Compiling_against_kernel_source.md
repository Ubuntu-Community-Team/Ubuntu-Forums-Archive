---
title: "Compiling against kernel source"
date: 2005-10-20
forum: General Help
---

### Post by med1972 on 2005-10-20
I am installing the Cisco VPN client software on my laptop. What package do I need in order to build it? I've managed to compile it before by installing a "bunch" of kernel related packages, but I am trying to keep my install clean so I'd like to know which package(s) I actually need to complete this.

```
mark@kiddo:~/Desktop/Downloads/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.03 (0190) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.12-9-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "" will be used to build the module.

Is the above correct [y]

```

I've already installed build-essentials.

Thanks,

Mark

---

### Post by Kyral on 2005-10-20
To compile against kernel source you need the headers package for your kernel

```
uname -r
```

To get the version of your kernel then 

```
sudo apt-get install linux-headers-<whatever uname -r gave you>
```

---

