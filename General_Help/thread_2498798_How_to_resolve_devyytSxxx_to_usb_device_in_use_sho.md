---
title: "How to resolve /dev/yytSxxx to usb device in use shown by lsusb?"
date: 2024-06-27
forum: General Help
---

### Post by makem2 on 2024-06-27
I have a Omron Corp. piece of equipment connect to a usb port to download data from the unit. When I choose to download the data I get an error:

Could not open serial port "/dev/ttySxxxx", Permission denied.

UFW is inactive

```

makem@makem-22:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 046d:c34a Logitech, Inc. LogiG TKL MKeyboard
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 005: ID 046d:c539 Logitech, Inc. Lightspeed Receiver
Bus 001 Device 006: ID 1038:12c4 SteelSeries ApS SteelSeries Arctis 9
Bus 001 Device 007: ID 0b05:19af ASUSTek Computer, Inc. AURA LED Controller
Bus 001 Device 008: ID 1038:12c2 SteelSeries ApS SteelSeries Arctis 9
Bus 001 Device 009: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 001 Device 010: ID 0590:0028 Omron Corp. HJ-720IT / HEM-7080IT-E / HEM-790IT   <<<<<<<<<<<<<<<<<<< Here I am
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
makem@makem-22:~$

```

I had assumed the device would therefore be on /dev/ttyS10 but nope, it's not

How do I find the correct /dev/ttySxxxx entry number for this usb port please? Then I can find out why permission is denied. (Maybe!). I have a choice of 50 possibilies.

---

### Post by #&amp;thj^% on 2024-06-27
What shows with:
```
ls -l /dev/usbmon*
```

---

### Post by Holger_Gehrke on 2024-06-27
USB serial devices are usually '/dev/ttyUSB*'. To find the right one you could either look at 'sudo dmesg' - there should be a message in there about the assignment of a device name to the USB-device - or look in '/sys/class/tty/'.

Holger

---

### Post by makem2 on 2024-06-27
> **1fallen said:**
> What shows with:
```
ls -l /dev/usbmon*
```

makem@makem-22:~$ ls -l /dev/usbmon*
ls: cannot access '/dev/usbmon*': No such file or directory
makem@makem-22:~$

---

### Post by makem2 on 2024-06-27
> **Holger_Gehrke said:**
> USB serial devices are usually '/dev/ttyUSB*'. To find the right one you could either look at 'sudo dmesg' - there should be a message in there about the assignment of a device name to the USB-device - or look in '/sys/class/tty/'.

Holger

Yes I looked in /sys/class/tty/

Didn't mean much to me - 10 = 10

---

### Post by makem2 on 2024-06-27
> **makem2 said:**
> Yes I looked in /sys/class/tty/

Didn't mean much to me - 10 = 10

Extract from dmsg:

```

makem@makem-22:~$
[19404.671972] usb 1-10: USB disconnect, device number 10
[19410.065561] usb 1-10: new low-speed USB device number 11 using xhci_hcd
[19410.198770] usb 1-10: New USB device found, idVendor=0590, idProduct=0028, bcdDevice= 2.01
[19410.198784] usb 1-10: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[19410.198790] usb 1-10: Product: HHX-CABLE-USB1
[19410.198794] usb 1-10: Manufacturer: OMRON Corporation
[19410.206568] hid-generic 0003:0590:0028.000E: hiddev6,hidraw12: USB HID v1.10 Device [OMRON Corporation HHX-CABLE-USB1] on usb-0000:00:14.0-10/input0
makem@makem-22:~$ 

```

No mention of ttySxxxxxx It needs to be /ttyS1 to 50 :-(

---

### Post by #&amp;thj^% on 2024-06-27
It was not running so give this a whirl:
```
sudo modprobe usbmon

```
Now it will/should show:
```
 lsmod | grep usbmon
usbmon                 45056  0

```

---

### Post by makem2 on 2024-06-27
Seems I may need to have a udev rule.

```

[21334.502221] usb 1-10: USB disconnect, device number 11
[21345.659397] usb 1-10: new low-speed USB device number 12 using xhci_hcd
[21345.792379] usb 1-10: New USB device found, idVendor=0590, idProduct=0028, bcdDevice= 2.01
[21345.792392] usb 1-10: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[21345.792398] usb 1-10: Product: HHX-CABLE-USB1
[21345.792402] usb 1-10: Manufacturer: OMRON Corporation
[21345.797423] hid-generic 0003:0590:0028.000F: hiddev6,hidraw12: USB HID v1.10 Device [OMRON Corporation HHX-CABLE-USB1] on usb-0000:00:14.0-10/input0

```

Is there enough info to make a rule?

---

### Post by makem2 on 2024-06-28
> **1fallen said:**
> It was not running so give this a whirl:
```
sudo modprobe usbmon

```
Now it will/should show:
```
 lsmod | grep usbmon
usbmon                 45056  0

```

It showed:

```

makem@makem-22:~$ sudo modprobe usbmon
[sudo] password for makem:
makem@makem-22:~$ lsmod | grep usbmon
usbmon                 45056  0
makem@makem-22:~$

```

I was about to revert to windows :-(

Until you returned :-)

---

### Post by makem2 on 2024-06-28
> **makem2 said:**
> I have a Omron Corp. piece of equipment connect to a usb port to download data from the unit. When I choose to download the data I get an error:

Could not open serial port "/dev/ttySxxxx", Permission denied.

UFW is inactive

```

makem@makem-22:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 046d:c34a Logitech, Inc. LogiG TKL MKeyboard
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 005: ID 046d:c539 Logitech, Inc. Lightspeed Receiver
Bus 001 Device 006: ID 1038:12c4 SteelSeries ApS SteelSeries Arctis 9
Bus 001 Device 007: ID 0b05:19af ASUSTek Computer, Inc. AURA LED Controller
Bus 001 Device 008: ID 1038:12c2 SteelSeries ApS SteelSeries Arctis 9
Bus 001 Device 009: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 001 Device 010: ID 0590:0028 [COLOR=#ff0000]Omron Corp. HJ-720IT / HEM-7080IT-E / HEM-790IT[/COLOR]   <<<<<<<<<<<<<<<<<<< Here I am
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
makem@makem-22:~$

```

I had assumed the device would therefore be on /dev/ttyS10 but nope, it's not

How do I find the correct /dev/ttySxxxx entry number for this usb port please? Then I can find out why permission is denied. (Maybe!). I have a choice of 50 possibilities.

I failed to notice that the line highlighted in red holds the necessary code to find the plug in required for the M10-IT BP monitor.

The plugin has the correct settings within it. It is not necessary to know the conversion I requested.

Thank you for your input

---

