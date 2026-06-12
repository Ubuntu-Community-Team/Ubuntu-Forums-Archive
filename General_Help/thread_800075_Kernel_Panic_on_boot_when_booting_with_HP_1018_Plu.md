---
title: "Kernel Panic on boot when booting with HP 1018 Plugged in to USB"
date: 2008-05-19
forum: General Help
---

### Post by doomzday on 2008-05-19
hi,
Im using ubuntu 8.04
my printer was working fine until I booted into MS, printed something there, when I got back to linux it didnt print anymore... 
I copied the firmware needed by the driver as all tutorials suggested but now when I boot my pc and the printer is connected I get kernel panic and my MS-os doesnt recognize.
if I plug the printer after booting ubuntu recognizes my printer but when I try to print the job sits there for a while and disappears (like the firmware problem)

here is my lsusb:
```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 045e:009d Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```
here is my /var/log/message when I plug the printer:
```
May 19 22:21:50 doron-desktop kernel: [   84.600429] usb 6-1: new high speed USB device using ehci_hcd and address 2
May 19 22:22:21 doron-desktop kernel: [  115.097500] usb 6-1: new high speed USB device using ehci_hcd and address 3
May 19 22:22:51 doron-desktop kernel: [  145.595582] usb 6-1: new high speed USB device using ehci_hcd and address 4
May 19 22:23:02 doron-desktop kernel: [  155.938035] usb 6-1: new high speed USB device using ehci_hcd and address 5

```

help ? :( I need to print my university assignments and now my printer is dead..

---

