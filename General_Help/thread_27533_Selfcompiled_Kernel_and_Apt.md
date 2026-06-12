---
title: "Selfcompiled Kernel and Apt"
date: 2005-04-16
forum: General Help
---

### Post by sys on 2005-04-16
Hello

I always compile my kernel for myself, and so I deinstalled linux-image and installed linux-source-2.6.10. I have some problems with this decision:

1. There is no package which depends on the most recent linux-source package, just like linux-image depends on the latest linux-image-xyz

2. I cannot easily install restricted modules for my w-lan pcmcia card, cause linux-restricted depends on linux-image, which I doesn't want to be installed...

fabian


PS: Another question: Isn't there a possibility of deinstalling anything I don't need, which ubuntu-base depends on, without deinstalling ubuntu-base and therefore missing any future updates?

---

### Post by nad on 2005-04-16
Welcome to the world of a managed distro. Apparently you wish to compile the module yourself, but as it is only available in restricted, the module is available as a binary only.

You can always force dependency issues with dpkg. You will be on your own here as you will no longer be running ubuntu.

Dan M

---

### Post by sys on 2005-04-16
No, I don't want to compile it myself. ;-)

I come from gentoo, and there was madwifi-driver an extra package which I could install, without having to install a kernel-image or something like that.

I'm sorry to say that, but what I saw until now about apt/dpkg, gentoo has a much better way of organizing and grouping packages together... :-)

fabian

---

### Post by nad on 2005-04-16
You could use a wrapper script: ' export LD_LIBRARY_PATH=/path/to/your/module ', before you load it, but you may have to force dependencies at the same time.

Dan M

---

### Post by az on 2005-04-16
"always compile my kernel for myself, and so I deinstalled linux-image and installed linux-source-2.6.10. I have some problems with this decision:"

You did not have to do this.  The madwifi driver is available in the restricted-modules package.  No need to compile anything.  I do not know why you did this.


"1. There is no package which depends on the most recent linux-source package, just like linux-image depends on the latest linux-image-xyz"

Yes, there is:
apt-cache show linux-image-386
Package: linux-image-386
Priority: optional
Section: base
Installed-Size: 48
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.10-7
Depends: linux-image-2.6.10-5-386
Filename: pool/main/l/linux-meta/linux-image-386_2.6.10-7_i386.deb
Size: 21670
MD5sum: 4cef851dd4a6a73dcbf5170de31596a8
Description: Linux kernel image on 386.
 This package will always depend on the latest kernel image available
 for 386.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


"2. I cannot easily install restricted modules for my w-lan pcmcia card, cause linux-restricted depends on linux-image, which I doesn't want to be installed..."

If you compiled your own kernel, a precompiled module would not work anyway!  Just install the linux-image you need and the restricted modules.


If there is another reason why you do not want a stock kernel, you can always build your driver with the source.

---

### Post by sys on 2005-04-17
1. I want to compile my kernel for myself, cause I want to decide what drivers to load etc....

2. this package depends on the latest linux-image, but not on latest  linux-source!!!

3. of course when the versions are the same this works, at least it worked for me the last one year :-)


My wishes: self-build Kernel of linux-source and binary module installed to it.

---

### Post by az on 2005-04-17
Try the linux-tree package

---

### Post by sys on 2005-04-17
Many Thanks, that's exactly what I was looking for! :-)

---

