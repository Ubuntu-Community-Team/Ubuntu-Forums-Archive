---
title: "Ubuntu 16.04 not finding bluetooth devices"
date: 2017-03-23
forum: General Help
---

### Post by Kornelia on 2017-03-23
Hi all,

Neither of my bluetooth headsets gets discovered when I search for them (my phone finds them with no issues). 
I have no clue what I'd need to do to get it sorted. I tried various suggestions I saw online but with no luck. It was a blind error and trial method as I don't know technical side of Ubuntu OS.
Any help would be greatly appreciated :-)

---

### Post by jeremy31 on 2017-03-23
Post results from terminal for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by Kornelia on 2017-03-23
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f3:21d4 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0a5c:6410 Broadcom Corp. 
Bus 001 Device 002: ID 045e:07a5 Microsoft Corp. Wireless Receiver 1461C
Bus 001 Device 005: ID 0c45:6713 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.194206] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    3.154587] Bluetooth: Core ver 2.21
[    3.154603] Bluetooth: HCI device and connection manager initialized
[    3.154605] Bluetooth: HCI socket layer initialized
[    3.154607] Bluetooth: L2CAP socket layer initialized
[    3.154611] Bluetooth: SCO socket layer initialized
[    3.160202] Bluetooth: HCI UART driver ver 2.3
[    3.160205] Bluetooth: HCI UART protocol H4 registered
[    3.160206] Bluetooth: HCI UART protocol BCSP registered
[    3.160207] Bluetooth: HCI UART protocol LL registered
[    3.160208] Bluetooth: HCI UART protocol ATH3K registered
[    3.160208] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.160244] Bluetooth: HCI UART protocol Intel registered
[    3.160254] Bluetooth: HCI UART protocol BCM registered
[    3.160255] Bluetooth: HCI UART protocol QCA registered
[    3.207265] Bluetooth: hci0: BCM: chip id 102
[    3.223257] Bluetooth: hci0: ChromeLinux_CCAA
[    3.225275] Bluetooth: hci0: BCM (001.001.005) build 0000
[    3.226389] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2
[    3.226393] Bluetooth: hci0: BCM: Patch brcm/BCM-0a5c-6410.hcd not found
[    3.334717] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac43602-pcie.txt failed with error -2
[    3.821807] brcmf_c_preinit_dcmds: Firmware version = wl0: Nov 10 2015 06:38:10 version 7.35.177.61 (r598657) FWID 01-ea662a8c
[    4.235294] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.235296] Bluetooth: BNEP filters: protocol multicast
[    4.235299] Bluetooth: BNEP socket layer initialized
[    8.791796] Bluetooth: RFCOMM TTY layer initialized
[    8.791801] Bluetooth: RFCOMM socket layer initialized
[    8.791804] Bluetooth: RFCOMM ver 1.11
[  327.220956] Bluetooth: Failed to start inquiry: status 18

```

---

### Post by jeremy31 on 2017-03-23
Download [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1589889/+attachment/4697483/+files/BCM-0a5c-6410_481.zip](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1589889/+attachment/4697483/+files/BCM-0a5c-6410_481.zip) 
Right click on the file and choose extract here.  Then right click in an open area in the folder and chose "open in terminal" and enter
```
sudo cp BCM-0a5c-6410.hcd /lib/firmware/brcm/
```

Reboot, some Broadcom bluetooth devices need firmware to enable various functionality

---

### Post by Kornelia on 2017-03-23
Excellent! Problem solved. Thank you very much :-)

---

