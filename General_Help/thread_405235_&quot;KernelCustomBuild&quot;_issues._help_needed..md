---
title: "&quot;KernelCustomBuild&quot; issues. help needed."
date: 2007-04-09
forum: General Help
---

### Post by noris2go on 2007-04-09
Hi,

I am trying to build the lirc kernel modules to match my installed kernel. I would prefer to install just these modules and not my full build if possible.

I followed the instructions from here:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

I am using the linux-source package 2.6.20 trying to match the preinstalled kernel 2.6.20-14-generic.

The debian/rules method fails for me with this error:
make: *** No rule to make target `binary-debs'.  Stop.
Any ideas what I need to do here ? I would prefer this method so I would get as close as possible with the official build.

I finally managed to build a very close package using this command:
UBUNTUBUILD=1 make-kpkg --initrd --append-to-version=-14-generic --revision 2.6.20 kernel-image

defining UBUNTUBUILD removes the default EXTRAVERSION ".3-ubuntu1" so my built version matches the installed version.

 the resulting package is though "linux-image-kdump_2.6.20_amd64.deb" any ideas how to remove the "kdump" from this and have a normal linux-image ?

Any help is much appreciated.
Thank you.

---

### Post by energiya on 2007-04-11
after make menuconfig (or "make xconfig" even "make gconfig" for a graphical version), in "General Setup" > "Local version - append to kernel release" I add "-my_string", then do the necessary configs and save. This is what I use (also remove --append-to-version and --revision).
Hope this helps.

---

### Post by noris2go on 2007-04-11
make menuconfig and unchecked this: 

[ ] kernel crash dumps (EXPERIMENTAL) 
 
in the: 

 Processor type and features  --->

did the trick.

Also a bunch of debug info options are checked.
I cannot believe that these options are checked by default.

---

### Post by energiya on 2007-04-12
> **noris2go said:**
> 
Also a bunch of debug info options are checked.
I cannot believe that these options are checked by default.

There is a lot of rubbish in the default kernel. Removing all that balast I earn about 12 seconds at boot time + a faster system.

---

