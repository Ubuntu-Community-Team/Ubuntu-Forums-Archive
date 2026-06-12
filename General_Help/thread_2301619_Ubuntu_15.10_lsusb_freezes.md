---
title: "Ubuntu 15.10 lsusb freezes"
date: 2015-11-03
forum: General Help
---

### Post by odror on 2015-11-03
Hi

After the upgrade to 15.10 when type lsusb it hangs. Even If I remove all the usb devices including the keyboard, but not the mouse. (I have only 1 ps/2 port)


strace lsusb:
```
munmap(0x7fa344ff3000, 4096)            = 0
open("/sys/bus/usb/devices/usb4/speed", O_RDONLY) = 6
fstat(6, {st_mode=S_IFREG|0444, st_size=4096, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fa344ff3000
read(6, "5000\n", 4096)                 = 5
close(6)                                = 0
munmap(0x7fa344ff3000, 4096)            = 0
open("/sys/bus/usb/devices/usb4/descriptors", O_RDONLY) = 6
read(6, 


```

sometime it hangs on /sys/bus/usb/devices/usb3/descriptors

Once it hangs CRTL-C does not help. it is stuck

(it either usb3 or usb4)

lsusb -t (works fine):
```
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/15p, 480M
    |__ Port 5: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 5: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 5: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 7: Dev 4, If 0, Class=Vendor Specific Class, Driver=, 12M

```


if I boot with the liveCd of 15.10 I do not have any problem.  Since I have the same kernel as in he LiveCD. It is probably not a kernel issue. I suspect that it is one of the services.

Any help will be appreciated.

---

### Post by samshepperd on 2015-12-16
I don't have any solutions but I did want to post that I have the exact same problem as you.  My lsusb hangs on open() usb4/descriptors

This is on kernel 3.13.0-73-generic on Ubuntu 14.04 LTS.  I am not sure exactly but I believe this started once Ubuntu started shipping/enabling UEFI kernels (vmlinuz-generic.efi.signed in /boot).  I tried falling back kernels and I can't get my usb working anymore so maybe that is not the problem.

In any case my USB sound has not worked for 2 months in Ubuntu due to this bug, very frustrating.

---

### Post by odror on 2015-12-17
I have solved the issue. The cause was a faulty USB3 PCI card. Once removed he problem was gone. I am guessing that in your case it is also a hardware issue that is related to USB.

---

