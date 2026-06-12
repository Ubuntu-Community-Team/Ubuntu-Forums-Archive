---
title: "Mounting an External HDD - Error -110"
date: 2016-05-03
forum: General Help
---

### Post by Peter_Kulcsr on 2016-05-03
Hi,

I have tried to mount my external HDD which is an older WD Red drive 2TB in i-tec external case. I have tried USB 2.0 and USB 3.0 slots too.

DMESG error:
[ 1338.206254] usb 1-1.1: new high-speed USB device number 7 using ehci-pci
[ 1348.409919] usb 1-1.1: New USB device found, idVendor=174c, idProduct=5106
[ 1348.409927] usb 1-1.1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 1348.409931] usb 1-1.1: Product: AS2105
[ 1348.409934] usb 1-1.1: Manufacturer: ASMedia
[ 1353.409667] usb 1-1.1: can't set config #1, error -110

Thanks for the help.

---

### Post by oldfred on 2016-05-03
We have seen several motherboards with Asmedia SATA ports and they do not work. Only the Intel SATA ports work and using Asmedia prevents entire system from working.

So I might be suspicious of the Asmedia comments.

We also have seen issues with some external cases. Some  do not work with USB3, Some do not work with gpt partitioned drives, and some do not work with large (over 2TiB) drives (which must be gpt, so maybe same issue).

Usual solution is just another USB case.

---

