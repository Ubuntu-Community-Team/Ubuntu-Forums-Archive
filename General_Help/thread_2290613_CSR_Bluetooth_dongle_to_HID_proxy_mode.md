---
title: "CSR Bluetooth dongle to HID proxy mode"
date: 2015-08-13
forum: General Help
---

### Post by Automat2 on 2015-08-13
Hi,

I am trying to find how to switch the actual HCI connection of this dongle to a HID.

Apparently there exists a BlueZ command to do this (hid2hci) but I don't see it in the list of programs available:
> bccmd, bluetooth-agent, bluetoothd, bluez-list-devices, bluez-simple-agent, bluez-simple-service, bluez-test-adapter, bluez-test-audio, bluez-test-device, bluez-test-discovery, bluez-test-input, bluez-test-manager, bluez-test-network, bluez-test-serial, bluez-test-service, bluez-test-telephony, ciptool, dfutool, gatttool, hciattach, hciconfig, hciemu, hcitool, l2ping, l2test, rctest, rfcomm, sdptool(From the Bluez Ubuntu Software Centre page)

Invoking hid2hci via terminal gives me no results.

I post the output of lsusb:

> jordi@jordi-desktop:~$ lsusb
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 006: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 005 Device 005: ID 08bb:2900 Texas Instruments PCM2900 Audio Codec
Bus 005 Device 004: ID 041e:4093 Creative Technology, Ltd 
Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 002: ID 050d:0307 Belkin Components USB 2.0 - 7 ports Hub [FSU307]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04e8:6123 Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



If anyone has a solution I'll be very grateful.

---

