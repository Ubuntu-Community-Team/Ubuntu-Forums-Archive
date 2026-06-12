---
title: "Amd-vi io_page_fault"
date: 2020-07-16
forum: General Help
---

### Post by bjcollin on 2020-07-16
Hello,

I have recently upgraded a PC (MSI 970 Gaming Motherboard) from ubuntu 18.04 server to 20.04 server by wiping the disk for a fresh install.  After the upgrade, I started receiving many error messages that were not present on the old server:

AMD-VI: Event logged [IO_PAGE_FAULT device=00.14.4 domain=0x000a address=0x0... flags=0x0000]

The only thing that keeps changing is the address with each error.

lspci -nn -vv   shows the 14.4 device to be:

00:14.4 PCI bridge [0604]: Advanced Micro Devices Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)


On the advice of another forum I tried a few renditions of adding the iommu=soft, iommu=pt, amd_iommu=on, etc to the /etc/default/grub file, followed by a sudo update-grub, but there was little effect on these error messages for any of these configurations.  iommu=soft seems to quiet the messages somewhat.

Any idea on why this would have the effect it has or how to fix this more properly?  Is there a driver I am missing or kernel module setting etc?  Thank you.


Brian Collins

---

