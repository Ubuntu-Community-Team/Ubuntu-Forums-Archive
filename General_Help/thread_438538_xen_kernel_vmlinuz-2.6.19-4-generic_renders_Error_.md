---
title: "xen kernel vmlinuz-2.6.19-4-generic renders Error 13"
date: 2007-05-09
forum: General Help
---

### Post by rmeglino on 2007-05-09
Error 13: Invalid or unsupported executable format

On ubuntu 7.04, after installing vmlinuz-2.6.19-4-generic using apt-get, I attempt to reboot into that kernel and get the Error 13 message. Nothing else happens and I must choose a different kernel.

Here's some info about my current system (IBM Thinkpad T42p):

ls /boot
abi-2.6.20-15-generic     grub                          initrd.img-2.6.20-15-generic.bak  System.map-2.6.20-15-generic
config-2.6.19-4-generic   initrd.img-2.6.19-4-generic   memtest86+.bin                    vmlinuz-2.6.19-4-generic
config-2.6.20-15-generic  initrd.img-2.6.20-15-generic  System.map-2.6.19-4-generic       vmlinuz-2.6.20-15-generic

/boot/grub/menu.lst:
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0e76b359-06eb-4d6a-a19b-f5dc55b7f71f ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0e76b359-06eb-4d6a-a19b-f5dc55b7f71f ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.19-4-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.19-4-generic dom0_mem=262144 root=UUID=0e76b359-06eb-4d6a-a19b-f5dc55b7f71f ro quiet splash
initrd          /boot/initrd.img-2.6.19-4-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.19-4-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.19-4-generic root=UUID=0e76b359-06eb-4d6a-a19b-f5dc55b7f71f ro single
initrd          /boot/initrd.img-2.6.19-4-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

dpkg -l | grep xen
ii  libc6-xen                                  2.5-0ubuntu14                              GNU C Library: Shared libraries [Xen version
ii  libxen3.0                                  3.0.3-0ubuntu10                            library interface for Xen, a Virtual Machine
ii  python-xen3.0                              3.0.3-0ubuntu10                            python bindings for Xen, a Virtual Machine M
ii  xen-docs-3.0                               3.0.3-0ubuntu10                            documentation for XEN, a Virtual Machine Mon
ii  xen-hypervisor-3.0-i386                    3.0.3-0ubuntu10                            The Xen Hypervisor for i386
ii  xen-image-2.6.19-4-generic                 2.6.19-2ubuntu7                            Linux 2.6.19 image on PPro/Celeron/PII/PIII/
ii  xen-tools                                  3.1-1ubuntu1                               Tools to manage debian XEN virtual servers
rc  xen-utils-3.0                              3.0.3-0ubuntu10                            XEN administrative tools
ii  xen-utils-common                           3.0.3-0-2                                  XEN administrative tools - common files
rc  xenman                                     0.5-2.1                                    A graphical Xen management tool

---

