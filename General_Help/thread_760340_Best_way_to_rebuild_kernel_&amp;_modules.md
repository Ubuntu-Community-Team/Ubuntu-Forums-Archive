---
title: "Best way to rebuild kernel &amp; modules?"
date: 2008-04-20
forum: General Help
---

### Post by Master One on 2008-04-20
I am a little confused right now. My problem is, that I have to patch the following kernel files, to get AGP support for the SiS Mirage*1 chipset of my Intel D201GLY2 mainboard:```
/drivers/char/agp/sis-agp
/drivers/char/drm/drm_pciids
/include/linux/pci_ids
```
That's the [iMedia kernel patch](http://www.linuxconsulting.ro/xorg-drivers/src/99-imedia-sis671-intelgly-2.6.23.patch), which applies just fine the the recent Hardy kernel sources.

I already recompiled my kernel according to the last entry on [this](https://wiki.ubuntu.com/KernelCustomBuild) page, and using the info from [here](https://help.ubuntu.com/community/Kernel/Compile).

My goal is, to just recompile the exact same kernel as installed by a standard Hardy installation, using the same EXTRAVERSION string, so that I can still use additional kernel modules from the Ubuntu repository without the need of rebuilding the linux-restricted-modules.

If I proceed the "The Old-Fashioned Debian Way", it works out fine, but in the end there seem to be some modules missing (like snd-intel8x0), and I have no idea, what went wrong.

The other two methods of getting the kernel source didn't work out for me, using the git-method just led to errors when proceeding with "AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic", and using "apt-get source linux-source" just downloaded a meta-package, but not the kernel sources themselves.

Just recompiling the kernel, and copying over sis-agp.ko, drm.ko and sis.ko also didn't work out.

So I am a little stuck right now. What is the best way, to simply apply a kernel patch, recompile kernel & modules (preferably with the same EXTRAVERSION, so just as a 1:1 replacement for the installed kernel-package), and install it, without anything missing?

---

