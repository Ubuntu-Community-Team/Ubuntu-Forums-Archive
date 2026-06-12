---
title: "reset high speed USB device using ehci_hcd"
date: 2008-01-20
forum: General Help
---

### Post by JSP on 2008-01-20
Hello,

With a few others, I have been having some trouble using some USB hard drives : when transferring large files, it stalls and the kernel reports "reset high speed USB device using ehci_hcd ..."

I found in various forums the following workarounds:
1/ remove the USB2.0 module :(
```
sudo rmmod ehci_hcd
```
but then you are back on USB1.1 transfer speed

2/ changing the max_sectors value :-?
```
sudo echo 1024 >/sys/block/sda/device/max_sectors
```
but it only allows you to transfer more data before the next reset occurs (at least on my lacie 160GB HDD)

3/ remounting with the sync option \\:D/
```
sudo mount -o remount,sync /dev/sda1
```
This one I believe is the correct fix - that I have actually found by using successfully the same HDD on a gentoo distribution.

Now question: 
Does anyone know how to change the automounting settings in order that the sync option is automatically added for a specific device ?

---

### Post by geraldm on 2008-01-20
The options can be stated in the fstab line for that device.
Look at the manpage for mount, under the "-o" option

Gerald

---

