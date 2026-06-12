---
title: "usb doesn't work after update 2.6.23.13 kernel"
date: 2008-01-14
forum: General Help
---

### Post by Alfie_Alfie on 2008-01-14
:confused: Well, i have no idea about it. After update to 2.6.23.13 kernel, when i connected flash drive on any usb port there was noting response. But when i connect it on windows it worked! so i tried to safety remove my flash drive on windows and reboot to ubuntu it was same nothing happen.
How can i fix this problem?

edit : i try to type lsusb in terminal but nothing showed, anyway another my printer work fine (connected with usb)

Sorry for my English.:(

---

### Post by Rog-Mahal on 2008-01-14
I am having a similar problem. My usb hard drive works fine, but a usb flash drive won't mount. I tried to boot with it plugged in and got the following error:

```
usb 1-3: device descriptor read/64, error -110
```

lsusb issues the following:

```
Bus 001 Device 013: ID 0d7d:1300 Phison Electronics Corp. Flash Disk
Bus 001 Device 005: ID 05ac:8300 Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 05ac:1000 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 05ac:8240 Apple Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05ac:021a Apple Computer, Inc. 
```

It seems like it's there, but it just won't mount. Any ideas?

---

