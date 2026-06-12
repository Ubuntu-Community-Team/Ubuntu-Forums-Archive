---
title: "USB Bluetooth dongle failure to connect"
date: 2024-01-30
forum: General Help
---

### Post by knight69 on 2024-01-30
I installed an ASUS USB-BT500 and the following software packages on my desktop computer using Ubuntu 22.04 desktop with gnome flashback:
   drivers downloaded from ASUS
   pulseaudio-module-bluetooth
   bluez
   blueez-tools
   blueman

lsusb shows bluetooth dongle at bus 001 device 008
systemctl status bluetooth shows that it is running
Pulseaudo control doesn't detect bluetooth as an output device
bluetooth icons (2) appear in upper panel with identical dropdown menus but when you click on devices or adapters, nothing appears
Blueman consistently shows 2 devices with unidentifiable mac addresses (that are different each time you launch the application) but nothing else and no information of any kind.

At this point, I cannot find a way to direct my audio through the bluetooth dongle, and if could I still wouldn't know how to connect to my earbuds Clearly I do not understand the bluetooth configuration and controls and cannot find any manual for Blueman. 

Any help on this would be greatly appreciated.

---

### Post by #&amp;thj^% on 2024-01-30
I'm assuming you have just installed "now" the driver from ASUS have you restarted bluetooth?
```
sudo systemctl restart bluetooth
```
if still no joy please include this:
```
hciconfig -a; sudo dmesg | egrep -i 'blue|firm'

```
I too have two devices ie:
```
hci1:	Type: Primary  Bus: USB
	BD Address: 5C:F3:70:A9:5B:DE  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN 
	RX bytes:2254 acl:0 sco:0 events:111 errors:0
	TX bytes:5835 acl:0 sco:0 commands:111 errors:0
	Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: PERIPHERAL ACCEPT 
	Name: 'me-on-zfs'
	Class: 0x6c010c
	Service Classes: Rendering, Capturing, Audio, Telephony
	Device Class: Computer, Laptop
	HCI Version: 4.0 (0x6)  Revision: 0x1000
	LMP Version: 4.0 (0x6)  Subversion: 0x220e
	Manufacturer: Broadcom Corporation (15)

hci0:	Type: Primary  Bus: USB
	BD Address: E0:0A:F6:81:81:92  ACL MTU: 1021:6  SCO MTU: 255:12
	UP RUNNING 
	RX bytes:3323 acl:0 sco:0 events:343 errors:0
	TX bytes:67832 acl:0 sco:0 commands:343 errors:0
	Features: 0xff 0xff 0xff 0xfe 0xdb 0xfd 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: PERIPHERAL ACCEPT 
	Name: 'me-on-zfs #1'
	Class: 0x6c010c
	Service Classes: Rendering, Capturing, Audio, Telephony
	Device Class: Computer, Laptop
	HCI Version: 5.2 (0xb)  Revision: 0xdac7
	LMP Version: 5.2 (0xb)  Subversion: 0x480d
	Manufacturer: Realtek Semiconductor Corporation (93)

[    0.094384] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.290010] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.311755] [Firmware Info]: PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] not reserved in ACPI motherboard resources
[    0.355627] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    2.636279] usb 3-4: Product: Bluetooth Radio
[    3.241493] [drm] Loading DMUB firmware via PSP: version=0x01010027
[    3.242026] [drm] Found VCN firmware Version ENC: 1.20 DEC: 6 VEP: 0 Revision: 0
[    3.242034] amdgpu 0000:05:00.0: amdgpu: Will use PSP to load VCN firmware
[    4.141075] scsi 2:0:0:0: Direct-Access     WD Blue  SN570 500GB      1.00 PQ: 0 ANSI: 6
[   26.226491] systemd[1]: systemd-pcrmachine.service - TPM2 PCR Machine ID Measurement was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/StubPcrKernelImage-4a67b082-0a4c-41cf-b6c7-440b29bb8c4f).
[   26.668756] Bluetooth: Core ver 2.22
[   26.668787] NET: Registered PF_BLUETOOTH protocol family
[   26.668789] Bluetooth: HCI device and connection manager initialized
[   26.668793] Bluetooth: HCI socket layer initialized
[   26.668796] Bluetooth: L2CAP socket layer initialized
[   26.668802] Bluetooth: SCO socket layer initialized
[   26.730343] Bluetooth: hci0: RTL: examining hci_ver=0b hci_rev=000a lmp_ver=0b lmp_subver=8852
[   26.731464] Bluetooth: hci0: RTL: rom_version status=0 version=1
[   26.731470] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_fw.bin
[   26.732790] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852au_config.bin
[   26.733246] Bluetooth: hci0: RTL: cfg_sz 6, total sz 61035
[   26.746231] rtw89_8852ae 0000:04:00.0: loaded firmware rtw89/rtw8852a_fw.bin
[   26.748402] rtw89_8852ae 0000:04:00.0: Firmware version 0.13.36.0 (c33d3f88), cmd version 0, type 1
[   26.748409] rtw89_8852ae 0000:04:00.0: Firmware version 0.13.36.0 (c33d3f88), cmd version 0, type 3
[   26.838281] Bluetooth: hci1: BCM: chip id 63
[   26.839268] Bluetooth: hci1: BCM: features 0x07
[   26.855276] Bluetooth: hci1: me-on-zfs
[   26.855281] Bluetooth: hci1: BCM20702A1 (001.002.014) build 0000
[   26.857614] Bluetooth: hci1: BCM: firmware Patch file not found, tried:
[   26.857618] Bluetooth: hci1: BCM: 'brcm/BCM20702A1-0b05-17cb.hcd'
[   26.857620] Bluetooth: hci1: BCM: 'brcm/BCM-0b05-17cb.hcd'
[   27.244315] Bluetooth: hci0: RTL: fw version 0xdac7480d
[   27.369317] Bluetooth: hci0: AOSP extensions version v1.00
[   27.369322] Bluetooth: hci0: AOSP quality report is supported
[   29.096608] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.096612] Bluetooth: BNEP filters: protocol multicast
[   29.096618] Bluetooth: BNEP socket layer initialized
[   29.103584] Bluetooth: MGMT ver 1.22
[   29.103670] Bluetooth: MGMT ver 1.22
[   35.912297] Bluetooth: RFCOMM TTY layer initialized
[   35.912311] Bluetooth: RFCOMM socket layer initialized
[   35.912318] Bluetooth: RFCOMM ver 1.11

```
My hardware:
```
lsusb | grep Bluetooth
Bus 001 Device 008: ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
Bus 003 Device 004: ID 0bda:4852 Realtek Semiconductor Corp. Bluetooth Radio

```

---

### Post by knight69 on 2024-01-30
I apologize for troubling you all. Don't ask me what I did or what happened, I have no idea. The bloody thing just started working.

---

