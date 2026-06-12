---
title: "kernel sources"
date: 2004-11-15
forum: General Help
---

### Post by danip on 2004-11-15
What directory are the kernel sources located in?  I am trying to set up vpn and its not where i thought they were located /usr/src/linux

---

### Post by anklator on 2004-11-15
u shouldnt be surprised, ubuntu doesnt install kernel sources by default, u should ge them by apt or kernel.org

---

### Post by nkdb on 2004-11-15
I have a question about kernel sources ...

Does kernel source ubuntu specification exist (so does "ubuntu .deb" package for kernel source exist ?), or with ubuntu we can compile kernel source from kernel.org ?

---

### Post by TravisNewman on 2004-11-15
[QUOTE=nkdb]I have a question about kernel sources ...

Does kernel source ubuntu specification exist (so does "ubuntu .deb" package for kernel source exist ?), or with ubuntu we can compile kernel source from kernel.org ?[/QUOTE]
 You can download deb packages with kernel source and patches, etc, with apt, yes, but you can also compile kernel source from kernel.org. Some people have had a few problems with compiling the ones from kernel.org, but it's possible.

---

### Post by az on 2004-11-15
"Does kernel source ubuntu specification exist"

install the kernel-source-2.6 package, untar it:
cd /usr/src
tar xvjf kernel-source*
cd kernel-source-2.6*

copy the config file you have in /boot that matches your running kernel.  Copy it to the kernel source tree as .config

---

### Post by danip on 2004-11-15
The vpn client says that i need the specific kernel built for my system.  Iam running 2.6.8.1-2.386 on here and I cannot find those sources on apt-get.  where else can i get them

---

### Post by Crisp on 2004-11-15
[QUOTE=danip]The vpn client says that i need the specific kernel built for my system.  Iam running 2.6.8.1-2.386 on here and I cannot find those sources on apt-get.  where else can i get them[/QUOTE]
 I think you're looking for [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/) but let me know if I misunderstood.

-Crisp

---

### Post by TravisNewman on 2004-11-15
[QUOTE=danip]The vpn client says that i need the specific kernel built for my system.  Iam running 2.6.8.1-2.386 on here and I cannot find those sources on apt-get.  where else can i get them[/QUOTE]
 You can get them with apt-get. The package you're looking for is:

linux-source-2.6.8.1

---

### Post by danip on 2004-11-15
ok well i got the source now im trying to install the client heres what happens.

```
blackbetty:/home/steve/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.0.1 (A) Linux Installer
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes] no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code [/usr/src/linux] /usr/src/linx/linux-2.6.8.1
Directory "/usr/src/linx/linux-2.6.8.1" doesn't exist

Directory containing linux kernel source code [/usr/src/linux] /usr/src/linux/linux-2.6.8.1/

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.8.1-2-386/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/usr/src/linux/linux-2.6.8.1/" will be used to build the module.

Is the above correct [y]

Making module
In file included from /usr/include/asm/smp.h:18,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/smp.h:17,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/sched.h:23,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/module.h:10,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/device.h:20,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/netdevice.h:38,                 from linuxcniapi.c:14:
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/src/linux/linux-2.6.8.1/include/linux/mm.h:15,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/skbuff.h:26,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/netdevice.h:151,
                 from linuxcniapi.c:14:
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h: In function `file_accessed':
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: `O_NOATIME' undeclared (first use in this function)
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: (Each undeclared identifier is reported only once
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: for each function it appears in.)
In file included from /usr/include/asm/smp.h:18,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/smp.h:17,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/sched.h:23,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/module.h:10,
                 from interceptor.c:13:
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/src/linux/linux-2.6.8.1/include/linux/mm.h:15,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/skbuff.h:26,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/netdevice.h:151,
                 from interceptor.c:16:
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h: In function `file_accessed':
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: `O_NOATIME' undeclared (first use in this function)
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: (Each undeclared identifier is reported only once
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: for each function it appears in.)
interceptor.c: In function `handle_vpnup':
interceptor.c:325: error: structure has no member named `next'
interceptor.c:330: error: structure has no member named `next'
In file included from /usr/include/asm/smp.h:18,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/smp.h:17,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/sched.h:23,
                 from IPSecDrvOS_linux.c:17:
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:18,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/smp.h:17,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/sched.h:23,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/module.h:10,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/device.h:20,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/netdevice.h:38,                 from frag.c:3:
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/src/linux/linux-2.6.8.1/include/linux/mm.h:15,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/skbuff.h:26,
                 from /usr/src/linux/linux-2.6.8.1/include/linux/netdevice.h:151,
                 from frag.c:3:
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h: In function `file_accessed':
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: `O_NOATIME' undeclared (first use in this function)
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: (Each undeclared identifier is reported only once
/usr/src/linux/linux-2.6.8.1/include/linux/fs.h:990: error: for each function it appears in.)
ld: cannot open frag.o: No such file or directory
Failed to make module "cisco_ipsec".

```

---

### Post by jeane123 on 2005-02-26
[QUOTE=danip]What directory are the kernel sources located in?  I am trying to set up vpn and its not where i thought they were located /usr/src/linux[/QUOTE]
 Did you ever get the Cisco VPN to work?? I am having the same issues?

Thank you 

JJ

---

### Post by danip on 2005-02-28
Nope still couldnt ever get it to work.  Let me know if you can.

---

### Post by jeane123 on 2005-03-03
Hi Danip, 

Use the vpnc package , It actually works!

JJ

---

