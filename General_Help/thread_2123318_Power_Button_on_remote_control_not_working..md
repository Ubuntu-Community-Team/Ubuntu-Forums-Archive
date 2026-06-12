---
title: "Power Button on remote control not working."
date: 2013-03-07
forum: General Help
---

### Post by Rebelli0us on 2013-03-07
I have a USB remote control for a Home Theater PC. In Windows it works, when I press the power button on the remote the machine suspends/resumes. But in Linux the power button on the remote control works **only once** after a fresh reboot. After that it does nothing. How can I get the power button working?

---

### Post by Rebelli0us on 2013-03-08
Does this help?

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 073a:2230 Chaplet Systems, Inc. infrared dongle for remote 
Bus 004 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 002: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 005 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
```


```
$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCE2	  S4	*disabled  
PCE3	  S4	*disabled  
PCE4	  S4	*disabled  pci:0000:00:04.0
PCE5	  S4	*disabled  
PCE7	  S4	*disabled  pci:0000:00:07.0
PCE9	  S4	*disabled  
PCEA	  S4	*disabled  
SBAZ	  S4	*disabled  pci:0000:00:14.2
P0PC	  S4	*disabled  pci:0000:00:14.4
UHC1	  S4	*enabled   pci:0000:00:12.0
UHC2	  S4	*enabled   pci:0000:00:12.2
USB3	  S4	*enabled   pci:0000:00:13.0
UHC4	  S4	*enabled   pci:0000:00:13.2
USB5	  S4	*enabled   pci:0000:00:16.0
UHC6	  S4	*enabled   pci:0000:00:16.2
UHC7	  S4	*enabled   pci:0000:00:14.5
PE20	  S4	*disabled  
PE21	  S4	*disabled  
PE22	  S4	*disabled  
PE23	  S4	*disabled  
GEC	  S4	*disabled  
PS2K	  S3	*enabled   pnp:00:09
PCE6	  S4	*disabled  pci:0000:00:06.0
PWRB	  S3	*enabled   
```

---

