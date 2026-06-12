---
title: "External HD not found on startup (12.04 LTS)"
date: 2014-06-01
forum: General Help
---

### Post by Robbyx on 2014-06-01
Gparted and the disk utility both can not see the External HD.
Mount -a produces a missing HD report when it comes to the UUID for the Ex HD partitions.
Lsub does not load as file is not found.
usbutils does not load for same reason and yet it is showing in synaptic as installed.

What do I do next to get the Ext hd to be recognised.

---

### Post by Robbyx on 2014-06-01
Here is some information that may help with a reply. Is my HD drive being shown up in this output?
NB USB 3 is the connection for the Ext HD. 

```

robins@robins-EP35-DS3L:~$ lsusb
Bus 001 Device 002: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 004 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 005 Device 002: ID 04f9:01b7 Brother Industries, Ltd MFC-5460CN Remote Setup Port
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 018: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 007: ID 046d:c247 Logitech, Inc. 
Bus 001 Device 019: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 020: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 001 Device 021: ID 03f0:a407 Hewlett-Packard 
Bus 001 Device 022: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 023: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


robins@robins-EP35-DS3L:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IB (ICH9) 4 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce 7600 GS] (rev a1)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
06:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI Audio (rev 10)
06:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)


robins@robins-EP35-DS3L:~$ dmesg | tail
[ 1120.672816] usb 1-3.1.3: New USB device found, idVendor=0d8c, idProduct=000c
[ 1120.672821] usb 1-3.1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[ 1120.672824] usb 1-3.1.3: Product: C-Media USB Headphone Set  
[ 1120.695869] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.3/input/input21
[ 1120.696114] hid-generic 0003:0D8C:000C.000C: input,hidraw5: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1a.7-3.1.3/input3
[ 1120.784068] usb 1-3.1.4: new full-speed USB device number 23 using ehci-pci
[ 1120.897823] usb 1-3.1.4: New USB device found, idVendor=0a12, idProduct=0001
[ 1120.897827] usb 1-3.1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1120.897830] usb 1-3.1.4: Product: Bluetooth V2.0 Dongle
[ 1120.897832] usb 1-3.1.4: Manufacturer: Bluetooth v2.0
robins@robins-EP35-DS3L:~$ 

```

---

### Post by Robbyx on 2014-06-01
This might be of help as well:

```
robins@robins-EP35-DS3L:~$ sudo mount -a
mount: special device UUID=13AC-9C9E does not exist
mount: special device UUID=23fcb4e3-c94e-44de-b7a9-105da58918c6 does not exist
mount: special device UUID=c99be12f-3a2d-4411-ab7c-5696167482dc does not exist
robins@robins-EP35-DS3L:~$ blkid
/dev/sda1: UUID="389c68f7-5a16-4625-aabe-02ede5569695" TYPE="swap" 
/dev/sda2: UUID="cfe95ef6-d1ab-4287-af5b-de922f30c40b" TYPE="ext4" 
/dev/sda5: LABEL="Home" UUID="803eff26-0660-46d4-8cbd-8f182f904ed5" TYPE="ext4" 
/dev/sda6: LABEL="mydocs" UUID="cb25d8db-9697-4245-acdd-90db9cf655c6" TYPE="ext4" 
/dev/sda7: LABEL="audio_visual" UUID="224b1762-f128-4b07-9039-a77bd2f4a7ef" TYPE="ext4" 
/dev/sdb1: UUID="E0D0-35DF" TYPE="vfat" 
robins@robins-EP35-DS3L:~$ 

```

---

### Post by fkkroundabout on 2014-06-01
does it work on another computer ?

^ the answer to that will solve whether your computer or the hard drive has the issue

---

### Post by Robbyx on 2014-06-01
Before I do that can you tell if the USB 3 card is being recognised? It is a Dynamode 4 Port Usb3.0 Pcie Card

---

### Post by Robbyx on 2014-06-01
At the moment I have it working. I could not see the USB 3 controller in the list of items under lspci above so I removed the controller, cleaned the terminals, and changed the power supply cable. When I put in the usb pci adapter it showed up in the output of lspci. It seems to have been successful because the drive was recognised as soon as I plugged in the usb cable! Mount -a loaded it and it is being recognised. Thanks for your help.

---

