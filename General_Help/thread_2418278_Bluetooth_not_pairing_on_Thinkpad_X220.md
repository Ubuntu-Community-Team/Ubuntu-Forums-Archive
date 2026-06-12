---
title: "Bluetooth not pairing on Thinkpad X220"
date: 2019-05-04
forum: General Help
---

### Post by toni-latenz on 2019-05-04
Hello everyone.

I am currently running Ubuntu 19.04 on my Lenovo Thinkpad X220. And i just can't get bluetooth working. It seems the hardware itself is working alright, but i can't find devices at all.

What i am trying to connect is a bluetooth headset (JBL) and/or the trackball-mouse "Logitech MX-Ergo".

First i tried in the Bluetooth - Tab of the settings. There, it always shows me a device "SL37" but never connects to it. I don't know what device this could be, as it is always listed, even if all my bt-devices are turned off.

[ATTACH=CONFIG]283185[/ATTACH]

Then i tried to connect a device via bluetoothctl, which seemed to find something (actually i don't know what..), but the authentication for pairing fails:
[ATTACH=CONFIG]283186[/ATTACH]

The command ```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

results in the following:

```
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    Subsystem: Lenovo ThinkPad T520 [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 (802.11a/b/g/n) [8086:1311]
    Kernel driver in use: iwlwifi
Bus 002 Device 003: ID 0bdb:1911 Ericsson Business Mobile Networks BV 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 04f2:b217 Chicony Electronics Co., Ltd Lenovo Integrated Camera (0.3MP)
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 004: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: Primary  Bus: USB
    BD Address: 40:2C:F4:56:48:23  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN 
    RX bytes:8642 acl:0 sco:0 events:981 errors:0
    TX bytes:7823 acl:0 sco:0 commands:372 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'toni-ThinkPad-X220'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 3.0 (0x5)  Revision: 0x2ec
    LMP Version: 3.0 (0x5)  Subversion: 0x4203
    Manufacturer: Broadcom Corporation (15)

[    0.132584] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.167703] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.189440] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    2.249901] usb 1-1.4: Product: Broadcom Bluetooth Device
[    2.984683] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    3.507024] Bluetooth: Core ver 2.22
[    3.507043] Bluetooth: HCI device and connection manager initialized
[    3.507047] Bluetooth: HCI socket layer initialized
[    3.507049] Bluetooth: L2CAP socket layer initialized
[    3.507052] Bluetooth: SCO socket layer initialized
[    3.533140] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.623094] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    4.741308] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.741310] Bluetooth: BNEP filters: protocol multicast
[    4.741314] Bluetooth: BNEP socket layer initialized
[    6.442194] audit: type=1400 audit(1556990472.883:62): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=876 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    6.464582] audit: type=1400 audit(1556990472.907:63): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=877 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[    6.482388] audit: type=1400 audit(1556990472.923:64): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=877 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    6.690246] audit: type=1400 audit(1556990473.131:65): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1173 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[    6.690487] audit: type=1400 audit(1556990473.131:66): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1173 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    6.694731] audit: type=1400 audit(1556990473.135:67): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1175 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    6.932238] audit: type=1400 audit(1556990473.375:68): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1232 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    6.933638] audit: type=1400 audit(1556990473.375:69): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1233 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[    6.933939] audit: type=1400 audit(1556990473.375:70): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1233 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    7.236469] audit: type=1400 audit(1556990473.679:71): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1276 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[  679.828236] Bluetooth: RFCOMM TTY layer initialized
[  679.828241] Bluetooth: RFCOMM socket layer initialized
[  679.828247] Bluetooth: RFCOMM ver 1.11
```

I currently have the Logitech USB-Dongle, which came with the trackball mouse connected, so i guess this is Bus 001 Device 006.

Latest version of Bluez is also installed, i checked that. 

Is there anything i can do? The hardware seems ok, right?
Would appreciate any help on this.

---

