---
title: "Stop driver in kernel?"
date: 2007-11-09
forum: General Help
---

### Post by Rick's Fork on 2007-11-09
I'm using Gutsy Gibbon and there is a driver in the kernel that loads for a RAID controller (with a Windows array configuration that is not supported (in Linux).  Gutsy takes over 5 minutes to load while it tries to mount drives on this controller.  It can't/doesn't mount the drives because they're part of a array that the Linux driver doesn't support.  Dmesg shows a bunch of bad block errors at boot.  This is array and controller is used only in Windows.  It is annoying that it takes so long to start Ubuntu, but mostly I'm concerned that at some point the Linux driver or Linux will try to correct what it sees as problems and corrupt the data on the array.  

It seems like there must be a way to keep this driver (that is part of the kernel) from loading.  I tried rebuilding the kernel without the driver, but I'm too much of a noobie and couldn't get it to work.  I had the same problem in Edgy Eft, and fixed the problem so it never happened again - even after kernel updates, but I don't remember what I did.  The driver name is "pata_sil680" in Gutsy, but I think it was called "siimage" in Edgy.. The driver name is not so relevant, but my question is more general:  How does one keep a driver from loading that is embedded in the linux kernel?  Thanks for any suggestions you have!

---

