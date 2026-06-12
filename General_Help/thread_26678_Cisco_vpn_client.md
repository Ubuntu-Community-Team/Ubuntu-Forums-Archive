---
title: "Cisco vpn client"
date: 2005-04-13
forum: General Help
---

### Post by luvdemheels on 2005-04-13
I am trying to install the cisco vpn client and it is asking the following:

"In order to build the VPN kernel module, you must have the kernel headers for the version of the kernel you are running."

It gives some example directories but I do not see anything there (/usr/src is at the front of all examples)

What path do I need to use??? THANKS for any help!!

---

### Post by shakin on 2005-04-13
Installing the 'linux-kernel-headers' package should fix you right up.

---

### Post by haxorwear on 2005-04-13
Depending on what version you are running... I had to do:

apt-get install linux-headers-`uname -r`

That got the correct headers package for my kernel revision (the default warty 2.6.8...

-Tim

---

### Post by luvdemheels on 2005-04-13
I tried /usr/include/linux and that did not work and I tried /usr/src/linux-headers-2.6.10-5 and no luck with that either. Any other suggestions.

Synaptic says linux-headers-2.6.10-5 and linux-kernel-headers are both installed.

---

### Post by luvdemheels on 2005-04-13
Here is the error:

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.10-5-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.10-5" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.10-5 SUBDIRS=/home/mydir/vpnclient modules
/usr/src/linux-headers-2.6.10-5/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-5/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5'
  CC [M]  /home/mydir/vpnclient/linuxcniapi.o
/bin/sh: gcc: command not found
make[2]: *** [/home/mydir/vpnclient/linuxcniapi.o] Error 127
make[1]: *** [_module_/home/mydir/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


Does anyone know what this means??? I think the problem has something to do with the gcc and command not found part.

---

### Post by diwakergupta on 2005-04-13
Why do you want CiscoVPN? Have you tried vpnc? (sudo apt-get install vpnc) -- vpnc is completely compatible with a lot of Cisco products (I use it on a daily basis, and its extremely robust and flexible). It needs no additional kernel modules either.

---

### Post by luvdemheels on 2005-04-13
Didn't know about it thanks, I will try it. Except now I have to setup my synaptic software sources. It only says cd and when I typed that command I got "E: Couldn't find package vpnc"

---

### Post by luvdemheels on 2005-04-13
I installed vpnc. How do I use it??

---

### Post by luvdemheels on 2005-04-13
Figured out vpnc and it is Great. I can be at home on my ubuntu linux laptop and administer my windows servers at work. Very nice. I have tested and it works Great!

 \\:D/

---

