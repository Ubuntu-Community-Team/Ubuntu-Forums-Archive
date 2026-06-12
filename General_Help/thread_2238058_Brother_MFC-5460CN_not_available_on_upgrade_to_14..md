---
title: "Brother MFC-5460CN not available on upgrade to 14.04."
date: 2014-08-05
forum: General Help
---

### Post by Robbyx on 2014-08-05
I have been using this printer as both a printer and scanner. I have no problems with it until today when it would not print from the computer.

 I can print out a test page if I do it from within the printer, but not from computer. I have reinstalled Brother's ubuntu drivers. 

I have changed the usb cable because I when I take it out, the computer crashes and restarts. 

I have run fsck -fyC on the sda drives. I have had a cross linking problem but that is now cleared  and there are no errors being reported when I run fsck.

lsub shows:

```
robins@robins-EP35-DS3L:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 2109:0811  
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 002: ID 04e8:6123 Samsung Electronics Co., Ltd 
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 007: ID 046d:c247 Logitech, Inc. 
Bus 001 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 009: ID 03f0:a407 Hewlett-Packard 
Bus 001 Device 006: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I can not see brother in the output.  

I have run a memory test and it seems ok. No errors.

I have tried [http://localhost:631](http://localhost:631) and nothing opens in the browser, but one of the brother drivers is a cups driver. 

What should I do next?

---

