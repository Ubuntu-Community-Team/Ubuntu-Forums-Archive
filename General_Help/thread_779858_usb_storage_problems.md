---
title: "usb storage problems"
date: 2008-05-03
forum: General Help
---

### Post by zxscooby on 2008-05-03
Im having problems with my usb flash drive.
 when i plug it in my dmesg says this

```
229.001854] [<ffffffff880b5d30>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  229.001876] Disabling IRQ #7
[ 7545.632743] usbcore: registered new interface driver libusual
[ 7545.638436] Initializing USB Mass Storage driver...
[ 7545.638547] usbcore: registered new interface driver usb-storage
[ 7545.638615] USB Mass Storage support registered.
[ 7997.690793] usb 2-1: new high speed USB device using ehci_hcd and address 2
[ 7999.913827] ehci_hcd 0000:00:0b.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[ 8006.587102] usb 2-1: device not accepting address 2, error -110
[ 8006.638446] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 8014.257508] usb 2-1: device not accepting address 3, error -110
[ 8014.305925] usb 2-1: new high speed USB device using ehci_hcd and address 4
[ 8020.917313] usb 2-1: device not accepting address 4, error -110
[ 8021.037112] usb 2-1: new high speed USB device using ehci_hcd and address 5
[ 8027.187034] usb 2-1: device not accepting address 5, error -110

```
if i boot the computer with the usb drive plugged in , it works
but i can only access it as su.
i cant seem to figure out whats wrong 
please help.
im guessin its something simple i dont know about

---

