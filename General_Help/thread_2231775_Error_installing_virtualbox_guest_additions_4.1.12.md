---
title: "Error installing virtualbox guest additions 4.1.12 on Lubuntu 14.04"
date: 2014-06-27
forum: General Help
---

### Post by brycenesbitt on 2014-06-27
On a fresh install of Lubuntu 14.04 under Virtual box, with guest additions 4.1.12 I get an error.
The log shows:


```

[LIST=1]
[*][COLOR=#000000]$ cat /var/log/vboxadd-install.log[/COLOR]
[*][COLOR=#000000]grep: /lib/modules/3.13.0-24-generic/build/include/linux/version.h: No such file or directory[/COLOR]
[*][COLOR=#000000]make KBUILD_VERBOSE=1 CONFIG_MODULE_SIG= -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules[/COLOR]
[*][COLOR=#000000]test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \[/COLOR]
[*][COLOR=#000000]        echo >&2;                                                       \[/COLOR]
[*][COLOR=#000000]        echo >&2 "  ERROR: Kernel configuration is invalid.";           \[/COLOR]
[*][COLOR=#000000]        echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\[/COLOR]
[*][COLOR=#000000]        echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";      \[/COLOR]
[*][COLOR=#000000]        echo >&2 ;                                                      \[/COLOR]
[*][COLOR=#000000]        /bin/false)[/COLOR]
[*][COLOR=#000000]...
/tmp/vbox.0/VBoxGuest-linux.c:206:49: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;g_VBoxGuestPciId&#8217;[/COLOR]
[*][COLOR=#000000] static const struct pci_device_id __devinitdata g_VBoxGuestPciId[] =[/COLOR]
[*][COLOR=#000000]                                                 ^[/COLOR]
[*][COLOR=#000000]In file included from /tmp/vbox.0/r0drv/linux/the-linux-kernel.h:78:0,[/COLOR]
[*][COLOR=#000000]                 from /tmp/vbox.0/VBoxGuest-linux.c:28:[/COLOR]
[*][COLOR=#000000]include/linux/module.h:88:32: error: &#8216;__mod_pci_device_table&#8217; aliased to undefined symbol &#8216;g_VBoxGuestPciId&#8217;[/COLOR]
[*][COLOR=#000000] extern const struct gtype##_id __mod_##gtype##_table  \[/COLOR]
[*][COLOR=#000000]                                ^[/COLOR]
[*][COLOR=#000000]include/linux/module.h:146:3: note: in expansion of macro &#8216;MODULE_GENERIC_TABLE&#8217;[/COLOR]
[*][COLOR=#000000]   MODULE_GENERIC_TABLE(type##_device,name)[/COLOR]
[*][COLOR=#000000]   ^[/COLOR]
[*][COLOR=#000000]/tmp/vbox.0/VBoxGuest-linux.c:216:1: note: in expansion of macro &#8216;MODULE_DEVICE_TABLE&#8217;[/COLOR]
[*][COLOR=#000000] MODULE_DEVICE_TABLE(pci, g_VBoxGuestPciId);[/COLOR]
[*][COLOR=#000000] ^[/COLOR]
[*][COLOR=#000000]make[2]: *** [/tmp/vbox.0/VBoxGuest-linux.o] Error 1[/COLOR]
[*][COLOR=#000000]make[1]: *** [_module_/tmp/vbox.0] Error 2[/COLOR]
[*][COLOR=#000000]make: *** [vboxguest] Error 2[/COLOR]
[*][COLOR=#000000]Creating user for the Guest Additions.[/COLOR]
[*][COLOR=#000000]Creating udev rule for the Guest Additions kernel module.[/COLOR]
[/LIST]

```

How can this be solved?


 /lib/modules/3.13.0-24-generic/build/include/linux/ contains vermagic.h, but not version.h

---

### Post by TheFu on 2014-06-28
Did you load the required dependencies before trying to do this?
[http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies](http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies)
Basically, 


To load the Guest Addition dependencies, start with:
[B]$ sudo apt-get install build-essential
[/B]
Then run uname -r to determine which kernel type is installed. Headers for your running kernel are needed.

    {something}-generic-pae = **sudo apt-get install linux-headers-generic-pae**
    {something}-generic = **sudo apt-get install linux-headers-generic**
    {something}-server = **sudo apt-get install linux-headers-server**
[B]
Only 1 of those should be installed.[/B]

---

### Post by SeijiSensei on 2014-06-28
I install VirtualBox from Oracle's repository following the method [described on the VirtualBox site]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian_based_Linux_distributions").  I've never had a problem with the guest additions using this approach.

---

### Post by brycenesbitt on 2014-06-29
I got it working.  None of the above did it for me.  I installed version 4.3.8 of the guest additions, after downloading from [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

---

