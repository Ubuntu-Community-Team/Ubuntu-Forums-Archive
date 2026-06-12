---
title: "Unable to install Cisco VPN"
date: 2006-10-18
forum: General Help
---

### Post by fillup on 2006-10-18
I recently installed Ubuntu 6.10 and now I am trying to install the Cisco VPN 4.8 client. For some reason it is not able to build the kernel module to install. Here is the output of the install script:

```

phillip@heat:~/downloads/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.17-10-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.17-10-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.17-10-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/phillip/downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/phillip/downloads/vpnclient/linuxcniapi.o
/home/phillip/downloads/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/phillip/downloads/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/phillip/downloads/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/phillip/downloads/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/phillip/downloads/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/phillip/downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

Any help would be much appreciated.

---

### Post by misha680 on 2006-10-19
I use network manager VPN plug-in. I've attached a copy of my checkinstalled version (it says 0.7.0 because it's CVS but it should work I think with other versions, although it might have some dependency probs because it is checkinstalled). Do a google search on the web to find the utility to decrypt the group passwords and you should be all set.

Misha

p.s. if it doesn't work, I actually made a howto on how to compile network manager CVS that also says how to compile the plug-in:

[http://www.ubuntuforums.org/showthread.php?t=235655](http://www.ubuntuforums.org/showthread.php?t=235655)

---

### Post by CheetahMk2 on 2006-10-20
Nice directions, thanks. But I am getting a problem.

I tried your addition, it applied, but as soon as I try to connect to my VPN the Network Manager applet dissapears and crashed. I've tried recompiling the CVS, ends up I get a 

The NetworkManager applet could not find some required resources. It cannot continue.

 error. Ends up it was complaining about an icon only, and I had to just use 

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

to fix it. But same problem after compiling the newest CVS versions of both Network-manager and network-manager-vpnc . As soon as I try to access the VPN, the tray icon dissapears and I can't log into the VPN. What could be causing this?

---

### Post by CheetahMk2 on 2006-10-20
Seems I needed a package from Synaptic called "dhcdbd". It referred me to some RedHat site, but it was there on Synaptic.

I also made the libnm-utils in the CVS and "make install"'ed it. I hope it doesn't break anything. I'm thinking there is some dependency that it isn't stating it needs.

Edit: Ok, I tried that, it didn't work. It still crashes into the deep blue yonder as soon as I try to run an actual VPN. No icon, no nothing. Grr...


I've tested and found 'NetworkManager' is what is crashing when I fire it up. NetworkManagerDispatcher and nm-applet seem to be chugging along just fine. ](*,) 

Any ideas?


*ignore that

I just was looking at the nm-vpnc-service.c and I realized something - this is looking for 

static const char *vpnc_binary_paths[] =
{
	"/usr/sbin/vpnc",
	"/sbin/vpnc",
	NULL
};

Meaning, it is DEPENDENT on the 'vpnc' package from synaptic, but that was never explicitly stated anywhere. I thought it was included in the network-manager-vpnc plugin. Let's try that and see...

**Final edit**
Well, that did it.

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

It now works. Sometimes, this damn OS is so simple it makes my head hurt. I'm going to start a new thread with full instructions top to bottom and the binaries I just compiled. Thanks for... listening to my thought process, I guess.

---

### Post by CheetahMk2 on 2006-10-20
Here are my binaries, freshly compiled. Just remember to do that icon re-registration trick if you get that Resources error

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

and remember to unisntall network-manager, network-manager-gnome, and libnm-util0 before installing. Also, you do need 'vpnc' from synaptic. I followed Misha's directions, more or less.

---

### Post by kipe on 2006-10-20
I'm sorry but why you didn't try this:
 $ sudo apt-get install vpnc kvpnc

---

### Post by harisund on 2006-10-25
> **fillup said:**
> I recently installed Ubuntu 6.10 and now I am trying to install the Cisco VPN 4.8 client. For some reason it is not able to build the kernel module to install. Here is the output of the install script:

```

phillip@heat:~/downloads/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.17-10-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.17-10-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.17-10-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/phillip/downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/phillip/downloads/vpnclient/linuxcniapi.o
/home/phillip/downloads/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/phillip/downloads/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/phillip/downloads/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/phillip/downloads/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/phillip/downloads/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/phillip/downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

Any help would be much appreciated.

In the file linuxcniapi.c, there are 2 references to skb->stamp (one in line 452, one in line 315). Now in the Linux Kernel 2.6 this has been changed to skb->tstamp. This needs to be fixed in order to get rid of the compilation errors.

I am just curious, what are you using your VPN client for? I am using mine to access my university resources (VPN into my univ. network from home). The Ubuntu crowd couldn't give me the answer I was looking for .... it was the Gentoo crowd :)

---

