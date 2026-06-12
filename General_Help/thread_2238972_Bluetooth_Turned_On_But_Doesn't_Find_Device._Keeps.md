---
title: "Bluetooth Turned On But Doesn't Find Device. Keeps Searching Forever."
date: 2014-08-11
forum: General Help
---

### Post by Thomas_Le on 2014-08-11
Title says it all. I have a Sager 9377 from xoticPC. I am running Ubuntu 14.04LTS. The Bluetooth Icon appears in the system tray area in the top right corner. I turn it on and go to 'Set up new device' when my device is in pairing mode and it just spins forever. I let it go for at least 5 minutes. I realize that if it doesnt pick it up (at least in my experience) in the first 10-20 seconds, it probably isn't going to pick it up but I let it go anyway to no avail.

```
uname -a
Linux sager-ubuntu 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

lspci

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 870M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
02:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 870M] (rev a1)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
05:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)

lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f2:b3e4 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 04f2:b42b Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 003 Device 009: ID 1b1c:0a0a Corsair 
Bus 003 Device 007: ID 1b1c:1b31 Corsair 
Bus 003 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

Any help/advice would be appreciated to get this to work.


_____________________________________________________________________

I did some additional digging and found some other commands to check.

```

hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 80:86:F2:19:F5:40  ACL MTU: 1021:5  SCO MTU: 96:5
    DOWN 
    RX bytes:1129 acl:0 sco:0 events:122 errors:0
    TX bytes:20643 acl:0 sco:0 commands:121 errors:0

```

That 'DOWN' is the key part. Even thought via the GUI menu in system settings it is turned on and in the system tray area in the top right corner it is turned on (sometimes they even mismatched). (I just checked again and they still mismatch. The top right corner has it toggled on and then clicking 'Bluetoooth Settings' it says it is 'OFF' on that menu screen. 

To turn on the bluetooth radio type

```

sudo hciconfig hci0 up

```

After doing this the status changed
```

hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 80:86:F2:19:F5:40  ACL MTU: 1021:5  SCO MTU: 96:5
    UP RUNNING 
    RX bytes:1699 acl:0 sco:0 events:152 errors:0
    TX bytes:21255 acl:0 sco:0 commands:151 errors:0

```

next, with the device on discovery mode type

```
 hcitool scan 
```

This outputs the name and MAC address of the device. Copy this down in a text box or something, you'll need it later.

I couldn't find the command via hcitool to add the device, which I am sure tehre is one. I tried **&#8203;hcitool --help** and from there I tried **hcitool lecc** which is labeled *Create a LE connection*. That didn't seem to do anything. It just timed out after a while. After finding another page, [https://help.ubuntu.com/community/BluetoothSetup#Setup_Devices](https://help.ubuntu.com/community/BluetoothSetup#Setup_Devices) I did a ```
sudo apt-get install bluez-compat
``` and used the hidd command ```
sudo hidd --connect AA:BB:CC:DD:EE
``` and it worked!

---

