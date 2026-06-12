---
title: "Edgy will NOT boot from USB!!!"
date: 2007-06-10
forum: General Help
---

### Post by hsuominen on 2007-06-10
I have tried everything and looked everywhere and i still cannot seem to get my new 2GB SanDisk Cruzer Micro drive to boot Ubutu 6.10 Edgy.

My bios is usb bootable and i have a fully working usb drive with pclinxos that works without problems.

I have bascially followed the tutorial at ([https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)) word for word and still nothing works. I have also searched google for answers but havent come up with anything useful.

I have tried rewriting the MBR using both install-mbr and lilo

I have tried both FAT16 and FAT32

The problem is that the usb drive is simply not detected at startup and my computer boots right into windows...

My biggest wonder is that my pclinux os usb drive works while my ubutu one does not. Effectively i have used the same version of syslinux on each so it cannot be due to that.

Ultimately this leaves us the drives themselves, the partions and filesystems (the one running pclinux os was never formatted in anyway, the files were simply copied over and syslinux took care of the rest), and the mbr... or smn else?

I would be very thankful for anyone able to point me in the right direction...

Henri

---

