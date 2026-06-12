---
title: "Help with running an installer script"
date: 2007-09-30
forum: General Help
---

### Post by jingdejun on 2007-09-30
Hi All,

I am completely new to Linux, so please forgive my simple question.

I just installed Ubuntu 7.10 (Gutsy Gibbon) on my new Lenovo T61 laptop. In order to use the campus wireless, I have to install the VPN software provided by the University.

I downloaded the Linux version of the VPN installation package. According to the installation guide, I unziped ithe package desktop, then run the installer script under terminal:
----------------------------------------------------------------------
Command:
~/Desktop/vpnclient$ [B]sudo ./vpn_install
[/B]

Results:
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]
return

Automatically start the VPN service at boot time [yes]
return

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-12-generic/build]
return

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-12-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-12-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-12-generic/build SUBDIRS=/home/zongzong/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-12-generic'
  CC [M]  /home/zongzong/Desktop/vpnclient/linuxcniapi.o
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/zongzong/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:297: warning: implicit declaration of function ‘skb_set_timestamp’
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/home/zongzong/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/home/zongzong/Desktop/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/zongzong/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/zongzong/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-12-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
 -------------------------------------------------------------------------

The error information pointed out what's the reason, but I don't know how to correct it.

Anyone can help me? Thanks a lot!!!

-Derek

---

### Post by ramjet_1953 on 2007-10-01
You may need to install build-essential first, as the script is using the make command.

[COLOR="Red"]sudo apt-get install build-essential
[/COLOR]
Regards,
Roger :cool:

---

### Post by jingdejun on 2007-10-01
Thanks for reply.

I installed build-essential first as you said, but still has same problem.

---

### Post by distroman on 2007-10-01
Not sure about this but you could give it a try.
```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by jingdejun on 2007-10-01
It still does not work.

Still hoping any input for solving this problem. Thanks in advance.

---

### Post by jingdejun on 2007-10-01
Solved by search google and got following article:

[http://tuxx-home.at/archives/2007/04/10/T15_55_43/](http://tuxx-home.at/archives/2007/04/10/T15_55_43/)

Looks like this is a typical problem associated with install CISCO VPN under Linux.

---

### Post by blakesle on 2007-10-05
> **jingdejun said:**
> Solved by search google and got following article:

[http://tuxx-home.at/archives/2007/04/10/T15_55_43/](http://tuxx-home.at/archives/2007/04/10/T15_55_43/)

Looks like this is a typical problem associated with install CISCO VPN under Linux.

I was able to download a new version of the Cisco VPN Client through the following link:

[http://tuxx-home.at/archives/2007/09/24/T15_26_49/](http://tuxx-home.at/archives/2007/09/24/T15_26_49/)

But in trying to get it going I ran into some different problems;:


Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-12-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-12-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.22-12-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-12-generic/build SUBDIRS=/home/blakesle/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-12-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.22-12-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST 1 modules
/bin/sh: scripts/mod/modpost: not found
make[2]: *** [__modpost] Error 127
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-12-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Can anyone offer some insights?

---

