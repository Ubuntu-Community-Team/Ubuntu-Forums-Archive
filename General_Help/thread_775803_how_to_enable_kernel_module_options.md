---
title: "how to enable kernel module options?"
date: 2008-04-30
forum: General Help
---

### Post by linuxd00 on 2008-04-30
hi
i have a Thiknpad X31.
In order to enable FN keys i have to use the thinkpad-acpi module
[http://ibm-acpi.sourceforge.net/](http://ibm-acpi.sourceforge.net/)
which is supposedly already built-in  in the kernel.
the PAge says:
"The ibm-acpi driver is part of the Linux kernel 2.6.10 and later (option CONFIG_ACPI_IBM)."

so how do i activate this Option?
 do i have to recompile the kernel? 

i watched into the Kernel configuration:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

and it says the IBM-ACPI is built in as a module.

i hope somebody can help. Right now im trying to recompile the kernel. In order to get Pentium-M optimization as well.It seems the standard Kernel is optimized for 486.
But in case i dont make it it would be cool to do this the safe way.

---

### Post by ryanhaigh on 2008-04-30
```
cat "/boot/config-`uname -r`" | grep CONFIG_ACPI_IBM
``` should tell you if the option is enabled, for me (gutsy) nothing comes up.

I don't know if its the right module but there is a acpihp_ibm module on my system, to load it simply do 
```
sudo modpobe acpihp_ibm
```

---

### Post by linuxd00 on 2008-04-30
hi, thanks
i also receive nothing on hardy

I browsed through my kernel configuration and there is an option for IBM ACPI.
Its flagged as <m> which seems to mean "loadable module".

so maybe there is a possibility to activate it.
[http://ubuntuforums.org/showthread.php?t=264057](http://ubuntuforums.org/showthread.php?t=264057)
says to put modules to be loaded in /etc/modules 
my machine has 

-------------------------------------
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
fuse
thinkpad_acpi fan_control=1
------------------------------------------------
so i wonder if this is enough?
but still i cant access my "access IBM" key


anyway right now im recompiling the kernel (for 2 hours now..) with Pentium M optimization (the standard kernel was set to 486) and i removed support for sony, Toshiba and HP Laptops which was enabled by default as well as support for "Amateur Radio" :D

i enabled also that IBM Module...


still i wonder how to turn this IBM ACPI on on the standard kernel...

i might upload my compiled kernel for all Thinkpad people once its ready.

The page says you get a .deb installer... so actually it seems easy to switch kernels.

---

### Post by ryanhaigh on 2008-04-30
To specify that you want a module loaded on startup just add it to /etc/modules

---

