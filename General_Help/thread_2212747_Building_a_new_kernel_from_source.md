---
title: "Building a new kernel from source"
date: 2014-03-22
forum: General Help
---

### Post by Johnathon_Galtman on 2014-03-22
I'm no newbie regarding linux, and have compiled tons of kernels many times.

But it's been awhile for ubuntu.

The info on various pages in the wiki is just not clear, like this page: [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

It assumes the reader knows where the directory "debian" is without stating it's path. Is it under the source tree? (I'm downloading the src now so can't look on my system yet)

I'm sure there's a convention I'm just not remembering for ubuntu (waaay back in the early days linux src was always located under /usr/local/linux or /usr/local/src/linux, a symlink to the particular kernel version tree), but when terms like "fakeroot" and "debian" are used they should be defined, at least on "newbie" oriented pages.

Also, I didn't see a more appropriate forum to post this in from those listed, so I hope this is the best place for this topic.

---------------

[COLOR=#000000]Getting all the prerequisite packages required to build the kernel is a pain. I tried using [/COLOR][https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)[COLOR=#000000] but it's not sufficient; I had to get ncurses-dev[el] for one example and kernel-package is another. Granted, the mythbuntu ISO is a purpose built distribution stripped of a lot of things, but the errors I'm dealing with just indicate "[/COLOR][COLOR=#333333]**apt-get build-dep linux-image-$(uname -r)**" does not provide all the tools / prerequisites required to rebuild the kernel from source as the wiki states.[/COLOR]

[COLOR=#000000]And when I run [/COLOR]
[COLOR=#333333]Code:
fakeroot debian/rules binary-headers binary-generic
[/COLOR][COLOR=#333333]it fails saying I need to run mrproper. _**But if I do it wipes the debian folder!**_
[/COLOR][COLOR=#000000]Code:
**...**
#
# configuration written to .config
#
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_64.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_x32.h
  SYSTBL  arch/x86/syscalls/../include/generated/asm/syscalls_32.h
  SYSHDR  arch/x86/syscalls/../include/generated/asm/unistd_32_ia32.h
  SYSHDR  arch/x86/syscalls/../include/generated/asm/unistd_64_x32.h
  SYSTBL  arch/x86/syscalls/../include/generated/asm/syscalls_64.h
  HOSTCC  arch/x86/tools/relocs
  Using /usr/linux-lts-raring-3.8.0 as source for kernel
  /usr/linux-lts-raring-3.8.0 is not clean, please run 'make mrproper'
  in the '/usr/linux-lts-raring-3.8.0' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/linux-lts-raring-3.8.0'
make: *** [/usr/linux-lts-raring-3.8.0/debian/stamps/stamp-prepare-tree-generic] Error 2
[/COLOR]
So why does using the mrproper make target remove the debian folder? What's my next step? I could try building the kernel without using the debian package builder but it would be nice if it worked as described in the wiki.

Not terribly surprising that incomplete information like this exists alongside other pages that provide more accurate instructions. This page: [https://help.ubuntu.com/lts/installation-guide/powerpc/kernel-baking.html](https://help.ubuntu.com/lts/installation-guide/powerpc/kernel-baking.html) is more up to date and provided some key information I needed to resolve these problems.

Being that I came up through the ranks back in the day when the Internet was used only for email and little else and the information was like gold and rarely duplicated, my expectations of obtaining information from it haven't adapted as rapidly as the Internet itself. I would hope that an open source community as big as Ubuntu would have people willing to kull the wiki pages to update & remove outdated information, but I guess not.

Perhaps I'll look into taking that on, at least for this topic, to do my part in improving the information for the next guy. Let this post be a start of that effort.

---

### Post by Doug S on 2014-03-23
I have struggled with that page also. Now, I generally compile the kernel straight from kernel.org, because I find it easier. To compile the Ubuntu kernel, my notes say "[Use the old fashioned way]("https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method:_The_Old-Fashioned_Debian_Way")". For what they are worth, my notes are:```
# Step 1 is to apt-get update and apt-get upgrade and apt-get dist-upgrade (if required)
# Step 2
#sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
# Step 3.1
#sudo apt-get build-dep linux
# Step 3.2
#sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
# Step 4.1
#sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
# Step 4.2
#apt-get source linux-image-$(uname -r)

cp /boot/config-3.12.0-4-generic .config  [COLOR=#ff0000]<<< whatever your kernel is[/COLOR]

<<<<< Note: check that CONFIG_DEBUG_INFO is not set. Typically it is set in Ubuntu devleopment stuff.

make clean
time make -j6 deb-pkg
time make -j8 deb-pkg LOCALVERSION=-round  [COLOR=#ff0000]<<< that is what I do for kernel.org kernels. Not tested yet.[/COLOR]
```

---

### Post by sammiev on 2014-03-23
> **Doug S said:**
> I have struggled with that page also. Now, I generally compile the kernel straight from kernel.org, because I find it easier. To compile the Ubuntu kernel, my notes say "[Use the old fashioned way]("https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method:_The_Old-Fashioned_Debian_Way")". For what they are worth, my notes are:```
# Step 1 is to apt-get update and apt-get upgrade and apt-get dist-upgrade (if required)
# Step 2
#sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
# Step 3.1
#sudo apt-get build-dep linux
# Step 3.2
#sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
# Step 4.1
#sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
# Step 4.2
#apt-get source linux-image-$(uname -r)

cp /boot/config-3.12.0-4-generic .config  [COLOR=#ff0000]<<< whatever your kernel is[/COLOR]

<<<<< Note: check that CONFIG_DEBUG_INFO is not set. Typically it is set in Ubuntu devleopment stuff.

make clean
time make -j6 deb-pkg
time make -j8 deb-pkg LOCALVERSION=-round  [COLOR=#ff0000]<<< that is what I do for kernel.org kernels. Not tested yet.[/COLOR]
```

Thanks Doug, I will likely give this a try.

---

