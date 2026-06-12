---
title: "Kernel build using fakeroot debian/rules"
date: 2015-03-30
forum: General Help
---

### Post by Alistair_Grant on 2015-03-30
I've been building the vanilla linux kernel without problems to correct
a driver issue with my Hauppauge USB-Live2 video capture device.  I'd now
like to build a kernel which matches the Ubuntu generic kernel as closely
as possible (plus the patch).


As an aside: If you have an Intel USB3 (xHCI) host controller and have been
having problems with isochronous devices, e.g. video capture devices, this
patch may help you.  See the details near the end of the message if you are
interested.


So far I've been compiling and installing the kernel with:


```
make -j4 INSTALL_MOD_STRIP=1
sudo make INSTALL_MOD_STRIP=1 modules_install install

```

without any issues.  And have also been able to build and install packages
using:


```
git am 0001-base-packaging.patch 
git am 0002-debian-changelog.patch 
git am 0003-configs-based-on-Ubuntu-3.19.0-10.10.patch 
git am xhci-pci.c-Lu-Baolu-apply-XHCI_AVOID_BEI-quirk-to-all-Intel-xHCI-controllers.patch 
make -j4 deb-pkg INSTALL_MOD_STRIP=1

```

However, my understanding is that I need to use the debian scripts to
properly build the Ubuntu kernel, i.e.:


```
fakeroot debian/rules clean
fakeroot debian/rules editconfigs
fakeroot debian/rules binary-generic

```

But the first step (clean) fails with:


```
+ '[' '!' -L ubuntu/vbox/vboxguest/include ']'
+ ln -sf ../include ubuntu/vbox/vboxguest/include
ln: failed to create symbolic link 'ubuntu/vbox/vboxguest/include': No such file or directory
+ '[' '!' -L ubuntu/vbox/vboxguest/r0drv ']'
+ ln -sf ../r0drv ubuntu/vbox/vboxguest/r0drv
ln: failed to create symbolic link 'ubuntu/vbox/vboxguest/r0drv': No such file or directory
+ '[' '!' -L ubuntu/vbox/vboxsf/include ']'
+ ln -sf ../include ubuntu/vbox/vboxsf/include
ln: failed to create symbolic link 'ubuntu/vbox/vboxsf/include': No such file or directory
+ '[' '!' -L ubuntu/vbox/vboxsf/r0drv ']'
+ ln -sf ../r0drv ubuntu/vbox/vboxsf/r0drv
ln: failed to create symbolic link 'ubuntu/vbox/vboxsf/r0drv': No such file or directory
+ '[' '!' -L ubuntu/vbox/vboxvideo/include ']'
+ ln -sf ../include ubuntu/vbox/vboxvideo/include
ln: failed to create symbolic link 'ubuntu/vbox/vboxvideo/include': No such file or directory
+ exit 0

```

I've got DKMS installed, and have searched the entire disk for "vboxvideo"
without success.

As a short term workaround, I'd be happy to disable the virtualbox support.


What am I doing wrong?


Thanks,
Alistair


For those interested in the patch:


Most, if not all, Intel USB3 (xHCI) host controllers need a quirk applied
(XHCI_AVOID_BEI) to function correctly with isochronous devices, typically
video or audio capture devices.


A patch has been proposed which corrects this problem, see
[http://www.gossamer-threads.com/lists/linux/kernel/2126922](http://www.gossamer-threads.com/lists/linux/kernel/2126922) for an
explanation and the patch, however it probably won't appear until kernel
4.1.  I've tested it successfully with the 3.19 kernel, it may or may not
work in earlier kernels (there have been progressive improvements to the
xHCI driver during the last 3 or 4 kernel releases).


This patch may help you if you see output from the following command:


```
lspci | grep -i xhci | grep Intel

```

e.g.


```
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)

```

---

### Post by Alistair_Grant on 2015-03-31
After much more searching around the web I've finally come up with a
successfully build sequence.  The main page which helped was:

[http://forum.xda-developers.com/general/general/guide-build-linux-kernel-source-t2882929](http://forum.xda-developers.com/general/general/guide-build-linux-kernel-source-t2882929)

The main difference is that instead of downloading the kernel source
directly from kernel.org and applying the patches, use the Ubuntu
repository.

```
sudo apt-get install gawk
# git clone git://kernel.ubuntu.com/ubuntu/ubuntu-<release>.git
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-vivid.git
cd ubuntu-vivid
# Apply any additional patches here
fakeroot debian/rules clean
# Create the config file(s).
# I only requested amd64, and initially made no changes in the config
# editor.
# Ignore all the errors from the unselected platforms.
fakeroot debian/rules editconfigs
# Do the actual build.
fakeroot debian/rules binary-headers binary-generic
cd ..
sudo dpkg -i linux-headers-3.19.0-10_3.19.0-10.10_all.deb 
sudo dpkg -i linux-headers-3.19.0-10-generic_3.19.0-10.10_amd64.deb 
sudo dpkg -i linux-image-3.19.0-10-generic_3.19.0-10.10_amd64.deb
sudo dpkg -i linux-image-extra-3.19.0-10-generic_3.19.0-10.10_amd64.deb

``` 


Hope this helps.

---

