---
title: "Intel hybrid graphics not detected, where best to put 13.04?"
date: 2013-04-23
forum: General Help
---

### Post by bogan on 2013-04-23
Hi!,** All**,      I have a new Desktop computer with an Intel i5 3570K 3.4GHz CPU and an Nvidia GTX 660 2Gb video card.

Windows 7 is installed in Legacy mode to the SSD and Ubuntu 12.10 & the GTX 660 run OK from an external HDD.
I am waiting for the 13.04 Release date before installing it directly.

I am puzzled that neither lspci, nor lshw, nor yet Windows Disk Manager, detect any integrated Video Adapter, only the GTX 660.
Though Computer Shopper says it should have Intel 4500 Hybrid graphics; or is that only for Laptops.??

So I have two questions:

1. If the CPU has integrated Graphics, and they were turned off in Bios/UEFI, would not lspci still detect them?

2. I have shrunk the sda Windows partition on the SSD to 55Gb - smallest permitted in Win Disk Manager - and used gparted to create a 44Gb Extended partition ready for Ubuntu. I have also created an Extended partition in the internal HDD.

Which is best ? To install 13.04 root to the SSD or to the HDD ?
If the first, then where should /home go ?  to the HDD ??

Chao!,** bogan.**

---

### Post by 3rdalbum on 2013-04-23
1. On the newer i5 CPUs, the Intel GPU is actually on the same die as the CPU. Therefore, it's quite logical that lspci would not detect something that's not connected through PCI :-)  Your GTX660 is a lot better than the Intel GPU so you're not missing out on anything. I don't believe it is hybrid graphics, I think it's just integrated graphics.

Other devices that connect via PCI may be invisible to all operating systems if turned off in the BIOS. It depends on implementation, but if the motherboard actually cuts power entirely to the PCI device then nothing will detect it.

2. Install 13.04 root (/) to the SSD and have /home on the hard disk. You don't need 44 gigs for / as that's more than twice as big as your / partition is likely to need.

---

### Post by bogan on 2013-04-23
Hi!, **3rdalbum**, Thanks for your response,

I was not surprised that lspci did not detect an integrated GPU, for, as you point out, it is not connected to a PCI slot, although I **have** **seen** lots of lspci outputs that do show it as a VGA adapter.

What did surprise me was that neither lshw nor hwinfo detected it either.

I did not realise that there was a difference between 'integrated' and 'hybrid' graphics, other than that the later implies the presence of a Video card in addition to the CPU graphics,w hereas the former my, or may not have one..

The 44Gb partition is an Extended one, and I will create smaller logical partitions within it, for Ubuntu, when I get round to installing 13.04.

Chao!,** bogan**.

---

