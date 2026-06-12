---
title: "Bluetooth - [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microc"
date: 2018-01-27
forum: General Help
---

### Post by vmdiezg on 2018-01-27
Hi there,

Laptop:Toshiba Satellite PRO C70-136
OS: Xubuntu 17.10

Bluetooth can't detect any devices.  And trying to diagnostic bt I got:

(I got and installed the lastest BIOS version from Toshiba before installing Xubuntu.)

```

$ lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Toshiba America Info Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1179:ff1e]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc BCM43142 802.11b/g/n [11ad:6655]
    Kernel driver in use: wl
Bus 001 Device 004: ID 0930:0225 Toshiba Corp. 
Bus 001 Device 003: ID 10f1:1a5b Importek 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: Primary  Bus: USB
    BD Address: B8:EE:65:94:3C:3D  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:1060 acl:0 sco:0 events:65 errors:0
    TX bytes:3962 acl:0 sco:0 commands:65 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'VD-SAT-PRO'
    Class: 0x10010c
    Service Classes: Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)

[    0.000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x20 (or later)
[    0.087525] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    8.019478] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[    8.417459] Bluetooth: Core ver 2.22
[    8.417479] Bluetooth: HCI device and connection manager initialized
[    8.417483] Bluetooth: HCI socket layer initialized
[    8.417486] Bluetooth: L2CAP socket layer initialized
[    8.417494] Bluetooth: SCO socket layer initialized
[    8.569965] Bluetooth: hci0: BCM: chip id 70
[    8.570958] Bluetooth: hci0: BCM: features 0x06
[    8.586953] Bluetooth: hci0: BCM43142A
[    8.586958] Bluetooth: hci0: BCM (001.001.011) build 0000
[    8.587761]** bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2**
[    8.587764] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    9.039698] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.039701] Bluetooth: BNEP filters: protocol multicast
[    9.039705] Bluetooth: BNEP socket layer initialized
[   10.592000] Bluetooth: hci0 command 0x1003 tx timeout
[   20.675519] Bluetooth: RFCOMM TTY layer initialized
[   20.675526] Bluetooth: RFCOMM socket layer initialized
[   20.675539] Bluetooth: RFCOMM ver 1.11

```

Any suggestion what are my options here?

---

### Post by managerceo1 on 2018-01-27
sudo apt-get install intel-microcode

and reboot.

Hope it helps.

---

### Post by oldos2er on 2018-01-27
Moved to General Help.

---

### Post by managerceo1 on 2018-01-27
[COLOR=#111111][FONT=Ubuntu]If it does not help, try to update your BIOS.[/FONT][/COLOR]

---

### Post by vmdiezg on 2018-01-27
Thanks managerceo1, it seems installing intel-microcode fixed firmware bug (or at least it's ignored) but bt stills unable to dectect any device

```

...
[    0.086813] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    8.006410] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[    8.278748] Bluetooth: Core ver 2.22
[    8.278772] Bluetooth: HCI device and connection manager initialized
[    8.278776] Bluetooth: HCI socket layer initialized
[    8.278778] Bluetooth: L2CAP socket layer initialized
[    8.278785] Bluetooth: SCO socket layer initialized
[    8.474486] Bluetooth: hci0: BCM: chip id 70
[    8.475435] Bluetooth: hci0: BCM: features 0x06
[    8.491441] Bluetooth: hci0: BCM43142A
[    8.491446] Bluetooth: hci0: BCM (001.001.011) build 0000
[    8.492448] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    8.492453] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    9.114524] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.114526] Bluetooth: BNEP filters: protocol multicast
[    9.114529] Bluetooth: BNEP socket layer initialized
[   10.523975] Bluetooth: hci0 command 0x1003 tx timeout
[   26.428029] Bluetooth: RFCOMM TTY layer initialized
[   26.428035] Bluetooth: RFCOMM socket layer initialized
[   26.428041] Bluetooth: RFCOMM ver 1.11

```

What it took me to continue investigating until I got here: (is it expected to have two BT devices?)


```

# rfkill list
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Also, I'm not quite sure if this should (or not) be blacklisted:

```

# grep -C2 b43 /etc/modprobe.d/blacklist.conf
blacklist prism54

# replaced by b43 and ssb.
# blacklist bcm43xx


```

---

### Post by jeremy31 on 2018-01-27
See [https://askubuntu.com/a/632348/300665](https://askubuntu.com/a/632348/300665) on how to convert the hex file from Windows drivers to BCM.hcd for linux

The two wireless and bluetooth devices is because of another kernel module, fairly common with Toshiba's

---

### Post by vmdiezg on 2018-01-28
Thanks a lot Jeremy31! The guide you linked worked as a charm! 
The BT is now able to detect and pair devices (after updated Broadcom drivers from the Windows ones). 

But now there is a  issue connecting the paired headset which I presume it will solve installing-updating bluesman (attached snapshot)
[ATTACH=CONFIG]278352[/ATTACH]

is it correct?

more info:

```

[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.InProgress
[NEW] Device 00:02:3C:38:D4:19 Creative WP-450 Headset
[bluetooth]# trust 00:02:3C:38:D4:19
[CHG] Device 00:02:3C:38:D4:19 Trusted: yes
Changing 00:02:3C:38:D4:19 trust succeeded
[bluetooth]# pair 00:02:3C:38:D4:19
Attempting to pair with 00:02:3C:38:D4:19
[CHG] Device 00:02:3C:38:D4:19 Connected: yes
[CHG] Device 00:02:3C:38:D4:19 UUIDs: 00001108-0000-1000-8000-00805f9b34fb
[CHG] Device 00:02:3C:38:D4:19 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 00:02:3C:38:D4:19 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 00:02:3C:38:D4:19 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 00:02:3C:38:D4:19 ServicesResolved: yes
[CHG] Device 00:02:3C:38:D4:19 Paired: yes
Pairing successful
[CHG] Device 00:02:3C:38:D4:19 ServicesResolved: no
[CHG] Device 00:02:3C:38:D4:19 Connected: no
[bluetooth]# connect 00:02:3C:38:D4:19
Attempting to connect to 00:02:3C:38:D4:19
Failed to connect: org.bluez.Error.Failed

```

---

