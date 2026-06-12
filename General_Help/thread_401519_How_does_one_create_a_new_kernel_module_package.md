---
title: "How does one create a new kernel module package?"
date: 2007-04-04
forum: General Help
---

### Post by Inuyaga on 2007-04-04
Ok so a search for "module package" "create module package" and several alterations there of; returns nothing useful. So what I need to find is some info on creating a package that when the kernel package updates it is a dependency and automatically updates to the current kernel. Im thinking (if possible) somehow hook the kernel package update and have a script run that updates the module package.
Anyway here is the what and why of what im trying to do.
I have a Promise EX8350 that I need the kernel to support on boot. So what I figure I will do is make a module for the driver and put it in the intraramfs. However when the kernel updates the driver module needs to be recompiled at least I think it does... Minimally it needs to be placed in the ramfs for that kernel.

These are the current steps that I had to take to get the driver loaded in the liveCD
[http://ubuntuforums.org/showthread.php?t=400858]("http://ubuntuforums.org/showthread.php?t=400858")
What I think I need the new package/script to do is this...
[On kernel update]
1) Grab kernel sources.
2) Copy current .config from /boot
3) run make modules_prepare
4) copy the modpost out of the script/mod to the current linux-headers/script/mod
5) run make KERNEL_SOURCE_DIR=/usr/src/linux-headers-(curver) on the current headers
6) shove it into the current ramfs
7) setup the new kernel to load the driver.

There is most likely a better way to do this but at the moment I have no idea what that is. Im going to look into the module's make file more and see if I can at least remove the modpost part.  The other thing I may be doing unnecessarily is recompiling the module every kernel update. Are modules compiled to 2.6.17-10 compatible with 2.6.17-11 and if so when do modules stop being compatible? Ive always recompiled everything (ex Gentoo user). For all I really know, under unbuntu, a module may be compatible on a 2.6.* level. Though its my experience that evreything should be recompiled evreytime to ensure maximum "its works".

For now im going to look into how dmraid does thing because it seems to load up in the intramfs and updates with the kernel. At least it seems to.

Thanks,
Inuyaga

---

