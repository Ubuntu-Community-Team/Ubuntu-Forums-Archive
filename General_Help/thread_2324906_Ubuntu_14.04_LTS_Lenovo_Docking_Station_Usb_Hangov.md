---
title: "Ubuntu 14.04 LTS Lenovo Docking Station Usb Hangover"
date: 2016-05-17
forum: General Help
---

### Post by densanki on 2016-05-17
Dear ubuntuforums community,

for work at my company i use ubuntu as os and try to solve any issue with.
After log search on google and other forum post I want to try here if someone can help me.

On working on the laptop the usb subsystem of ubuntu is making a hangover. So all usb slots on dock and direct on laptop going offline.
So its very unnice when you try to work and usb mouse and keyboard aren't working any more.
Strange on this is the keyboard and touchpad on laptop included are working.

I working with virtualbox and genymotion for run virtual devices, thats my first idee when I have problems. But I'm not sure where to search.

When boot up the laptop on dock and work everything works and lsusb gives output.
After time x (not sure happen early or midday) then usb devices stopping working. And when I read out lsub is hanging on output.

lsusb when it works:
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 5986:026a Acer, Inc 
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 138a:0017 Validity Sensors, Inc. Fingerprint Reader
Bus 002 Device 002: ID 1199:a001 Sierra Wireless, Inc. 
Bus 002 Device 006: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/9p, 480M
    |__ Port 1: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 1: Dev 6, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 4: Dev 2, If 0, Class=Communications, Driver=cdc_mbim, 480M
    |__ Port 4: Dev 2, If 1, Class=CDC Data, Driver=cdc_mbim, 480M
    |__ Port 4: Dev 2, If 2, Class=Communications, Driver=cdc_acm, 480M
    |__ Port 4: Dev 2, If 3, Class=CDC Data, Driver=cdc_acm, 480M
    |__ Port 6: Dev 3, If 0, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 7: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 7: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 8: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 8: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 5: Dev 3, If 0, Class=Chip/SmartCard, Driver=, 12M

I only need a hint where to search and what I can try next.

Thank you for and hint and analyse step in advance.

---

### Post by densanki on 2016-05-23
Add some syslog I found some strange usb informations when usb port switch offline.

May 23 15:44:02 gerlando-ThinkPad-T440s kernel: [26392.082118] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:02 gerlando-ThinkPad-T440s kernel: [26392.098129] usb 2-3-port4: cannot disable (err = -71)
May 23 15:44:02 gerlando-ThinkPad-T440s kernel: [26392.098241] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.074847] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.074911] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075007] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075096] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075128] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075129] usb 2-3-port2: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075212] usb 2-3-port2: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075289] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075369] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075449] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075530] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075610] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075612] usb 2-3-port2: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075689] usb 2-3-port2: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.075776] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.076765] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077104] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077152] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077230] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077232] usb 2-3-port2: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077345] usb 2-3-port2: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077537] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077631] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077777] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.077813] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078094] usb 2-3-port2: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078096] usb 2-3-port2: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078131] usb 2-3-port2: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078306] usb 2-3-port2: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078383] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078435] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078459] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078531] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078610] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078686] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078854] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078855] usb 2-3-port3: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.078886] usb 2-3-port3: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079169] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079216] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079488] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079520] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079598] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079600] usb 2-3-port3: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079678] usb 2-3-port3: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079758] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079838] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079927] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.079999] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080078] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080079] usb 2-3-port3: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080158] usb 2-3-port3: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080238] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080318] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080398] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080477] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080557] usb 2-3-port3: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080559] usb 2-3-port3: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080637] usb 2-3-port3: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080717] usb 2-3-port3: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080801] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080879] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.080971] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.086729] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.086842] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.086896] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.086950] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087001] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087002] usb 2-3-port1: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087029] usb 2-3-port1: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087109] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087190] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087269] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087349] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087429] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087430] usb 2-3-port1: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087509] usb 2-3-port1: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087589] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087669] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087749] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087829] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087909] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087910] usb 2-3-port1: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.087989] usb 2-3-port1: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088069] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088149] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088229] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088307] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088389] usb 2-3-port1: cannot reset (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088390] usb 2-3-port1: Cannot enable. Maybe the USB cable is bad?
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088469] usb 2-3-port1: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088549] usb 2-3-port1: cannot disable (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088663] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088723] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088802] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:03 gerlando-ThinkPad-T440s kernel: [26393.088882] hub 2-3:1.0: hub_port_status failed (err = -71)
May 23 15:44:09 gerlando-ThinkPad-T440s kernel: [26399.612235] usb 2-3.1: USB disconnect, device number 18

---

