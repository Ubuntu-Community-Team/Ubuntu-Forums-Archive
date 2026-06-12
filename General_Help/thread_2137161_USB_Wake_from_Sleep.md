---
title: "USB Wake from Sleep"
date: 2013-04-19
forum: General Help
---

### Post by itsacoaster on 2013-04-19
Hi everyone.

I have a Dell Latitude 620 laptop, using Lubuntu 12.10 (it's great!), and I want to be able to wake my computer from suspend using a USB keyboard or mouse.  Right now it does not--not even the laptop's built in keyboard or mouse wakes up the machine.

I checked the BIOS and wake from USB was disabled.  I enabled it and still no USB device or the built-in keyboard/mouse would resume.

So I did some searching and saw to check the results of a few commands.  By any chance can you folks make any determinations using this?  I've searched and searched and I'm hoping you folks can help as a last resort.

cat /proc/acpi/wakeup
```
Device	S-state	  Status   Sysfs node
LID	  S3	*enabled   
PBTN	  S4	*enabled   
PCI0	  S5	*disabled  no-bus:pci0000:00
USB0	  S3	*enabled   pci:0000:00:1d.0
USB1	  S3	*enabled   pci:0000:00:1d.1
USB2	  S3	*enabled   pci:0000:00:1d.2
USB3	  S3	*enabled   pci:0000:00:1d.3
EHCI	  S3	*enabled   pci:0000:00:1d.7
AZAL	  S3	*disabled  pci:0000:00:1b.0
PCIE	  S4	*disabled  pci:0000:00:1e.0
RP01	  S3	*disabled  pci:0000:00:1c.0
RP02	  S4	*disabled  pci:0000:00:1c.1
NIC	  S5	*enabled   pci:0000:09:00.0
RP04	  S3	*disabled  
RP05	  S3	*disabled  
RP06	  S3	*disabled  
```

So as you can see it seems as though USB resume is enabled for USB devices, yet it doesn't work.
In the following, the **Holtek Semiconductor, Inc.** device is the one I want to wake up the machine.  I checked "cat /sys/bus/usb/devices/3-2/power/wakeup" and it returned "enabled."
I'm not sure how to figure out which device is the laptop's built-in input device.

lsusb
```
Bus 001 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 003 Device 002: ID 04d9:2519 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
```

lsusb -t
```
2-2.3.1:1.0: No such file or directory
2-2.3.2:1.0: No such file or directory
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 2: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 12M
        |__ Port 3: Dev 3, If 0, Class=hub, Driver=hub/3p, 12M
            |__ Port 1: Dev 4, If 0, Class=vend., Driver=, 12M
            |__ Port 2: Dev 5, If 0, Class=scard, Driver=, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 6: Dev 4, If 0, Class=vend., Driver=ndiswrapper, 480M
```

---

### Post by Rebelli0us on 2013-04-20
Linux doesn't yet have a friendly user interface for wakeup settings. All you need is a one-line-file in /etc/udev/rules.d/

[Use this]("http://bernaerts.dyndns.org/linux/220-ubuntu-resume-usb-hid"), it recognizes all devices in your system and simply works.

---

### Post by itsacoaster on 2013-04-21
Unfortunately that didn't work.  I still can't wake the system with anything but the power button.  Not even the laptop keyboard or mouse works.

Edit:  I should mention that opening the laptop lid also works to wake the system.

If for some reason we can't figure out how to get anything else to work, the laptop lid solution would probably do, but I'm trying to set up this laptop as a HTPC for the moment, and ideally I'd like to wake it with the wireless keyboard if that's possible.

---

### Post by Rebelli0us on 2013-04-23
Why didn't it work?  There are 2 scripts, one lets you select the resume device(s), the other one enables wakeup for devices you've selected. You only need to run it once, and once you've created the 2 files you can copy them to any machine. You just need to copy/paste the code and make the scripts executable.

---

