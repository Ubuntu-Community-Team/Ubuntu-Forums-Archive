---
title: "On-board USB ports not working"
date: 2013-02-24
forum: General Help
---

### Post by Garrett87 on 2013-02-24
I am new to Linux and Ubuntu, I like the layout, and I'm finding good information in the forums. I am having trouble finding the specific issue with my USB ports. I installed Ubuntu 12.10 on my new computer, and only two USB ports are working properly. 

lsusb output: 
```
Bus 008 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 008 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

Unfortunately I am using a wireless internet dongle in one port and a mouse in the other so if I want to use any other device I will have to sacrifice one of those two. I have an external hard drive plugged into the front port, it spins up and the light comes on but it doesn't show up anywhere in ubuntu. I can plug that same hard drive into either one of the two ports that work (Bus 008) and it works fine. I can also boot Ubuntu from a flash drive plugged into other ports so I don't think its a BIOS issue. I am not sure where to start, everywhere I have searched has lead to a rabbit trail, and I cannot find a solution.

lsusb -t output:
```
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 2: Dev 3, If 0, Class=vend., Driver=ath9k_htc, 480M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/4p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/5p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/5p, 480M
```

Im thinking this may be what the issue is, Bus 08's driver is xhci_hcd/2p, and the other ports appear to be using a different driver, but I am not entirely sure what im looking at here, or where to go next to find a solution. Any help on solving this would be greatly appreciated. 

dmesg output: 
```
[ 1196.731398] usb 5-1: new full-speed USB device number 14 using ohci_hcd
[ 1196.870995] usb 5-1: device descriptor read/64, error -32
[ 1197.114297] usb 5-1: device descriptor read/64, error -32
[ 1197.353613] usb 5-1: new full-speed USB device number 15 using ohci_hcd
[ 1197.493209] usb 5-1: device descriptor read/64, error -32
[ 1197.736513] usb 5-1: device descriptor read/64, error -32
[ 1197.975822] usb 5-1: new full-speed USB device number 16 using ohci_hcd
[ 1198.382650] usb 5-1: device not accepting address 16, error -32
[ 1198.518268] usb 5-1: new full-speed USB device number 17 using ohci_hcd
[ 1198.925092] usb 5-1: device not accepting address 17, error -32
[ 1198.925110] hub 5-0:1.0: unable to enumerate USB device on port 1
```

---

### Post by elliotn on 2013-02-25
buy those 4 in 1 USB ports

---

### Post by Garrett87 on 2013-02-25
I guess I could do that as a last resort, but I really would like to know if there is any tweak that would easily resolve this.

---

### Post by dcstar on 2013-02-26
> **Garrett87 said:**
> I guess I could do that as a last resort, but I really would like to know if there is any tweak that would easily resolve this.

Check your BIOS settings for any USB hardware options.

---

### Post by Garrett87 on 2013-02-27
I checked in the BIOS settings and it had an echi setting, I turned that on and gave it a try, but there was no difference. Still only the two USB ports are working...

---

### Post by Garrett87 on 2013-03-03
I am up and running now. I changed the BIOS settings for "ECHI Hand Off" to enabled, started Ubuntu, opened terminal, update-usbids, and now my usb ports are working.

---

### Post by dcstar on 2013-03-03
> **Garrett87 said:**
> I am up and running now.


Then MARK the thread.

---

