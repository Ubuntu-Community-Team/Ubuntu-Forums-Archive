---
title: "Bluetooth not being recognized by other devices"
date: 2015-04-24
forum: General Help
---

### Post by bach on 2015-04-24
I instaled Ubuntu 15.04 on a DELL XPS 13 notebook (model 9343). My internal bluetooth device is detected with hci, the icon is in the taskbar, but when scanning for bluetooth devices it finds nothing and it itself cannot be found. I am attaching some info. Suggestions are welcome. 

cribari@darwin4:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux darwin4 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell Device [1028:0019]
	Kernel driver in use: wl
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0c45:670c Microdia 
Bus 001 Device 004: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 002: ID 046d:c530 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.136553] Bluetooth: Core ver 2.20
[    2.136568] Bluetooth: HCI device and connection manager initialized
[    2.136572] Bluetooth: HCI socket layer initialized
[    2.136575] Bluetooth: L2CAP socket layer initialized
[    2.136581] Bluetooth: SCO socket layer initialized
[    2.138896] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
[    2.138899] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[    3.407444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.407448] Bluetooth: BNEP filters: protocol multicast
[    3.407452] Bluetooth: BNEP socket layer initialized
[    3.413492] Bluetooth: RFCOMM TTY layer initialized
[    3.413499] Bluetooth: RFCOMM socket layer initialized
[    3.413504] Bluetooth: RFCOMM ver 1.11
[    2.138896] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0a5c-216f.hcd failed with error -2
bluetooth             491520  22 bnep,btusb,rfcomm
cribari@darwin4:~$

---

