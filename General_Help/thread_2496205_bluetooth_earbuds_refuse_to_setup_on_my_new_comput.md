---
title: "bluetooth earbuds refuse to setup on my new computer but worked on old."
date: 2024-03-18
forum: General Help
---

### Post by 0cs935-bill on 2024-03-18
Although I’m not reporting a bug, only asking for assistance, I’m supplying the information mentioned for bug reporting here :
[https://wiki.ubuntu.com/DebuggingBluetooth](https://wiki.ubuntu.com/DebuggingBluetooth)


The problem concerns earbuds **0B:20:24:A3:E7:56 T60** that worked perfectly under completely patched Ubuntu 22.04 on my old machine but now refuse to be setup on a new box running completely patched Ubuntu 22.04 . Other old bluetooth gadgets attached without issue.

The end result at the very bottom of this page indicates  ‘requestor exited before bonding was completed’ . What could be causing this and is there anything I can do to fix it?




root@bill:~# bluetoothctl --version
bluetoothctl: 5.64
root@bill:~# hciconfig -a
hci0:	Type: Primary  Bus: USB
	BD Address: BC:C7:46:9D:25:98  ACL MTU: 1021:8  SCO MTU: 255:12
	UP RUNNING PSCAN 
	RX bytes:11627 acl:0 sco:0 events:466 errors:0
	TX bytes:78563 acl:0 sco:0 commands:422 errors:0
	Features: 0xff 0xff 0xff 0xfe 0xdb 0xfd 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: PERIPHERAL ACCEPT 
	Name: 'bill'
	Class: 0x7c0104
	Service Classes: Rendering, Capturing, Object Transfer, Audio, Telephony
	Device Class: Computer, Desktop workstation
	HCI Version:  (0xc)  Revision: 0x40d
	LMP Version:  (0xc)  Subversion: 0x7225
	Manufacturer: Realtek Semiconductor Corporation (93)


root@bill:~# bluetoothctl
Agent registered
[CHG] Controller BC:C7:46:9D:25:98 Pairable: yes
[bluetooth]# show
Controller BC:C7:46:9D:25:98 (public)
	Name: bill
	Alias: bill
	Class: 0x007c0104
	Powered: yes
	Discoverable: no
	DiscoverableTimeout: 0x000000b4
	Pairable: yes
	UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
	UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
	UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
	UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
	UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
	UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
	UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
	UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
	UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
	UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
	UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
	UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
	UUID: Handsfree Audio Gateway   (0000111f-0000-1000-8000-00805f9b34fb)
	UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
	UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
	Modalias: usb:v1D6Bp0246d0540
	Discovering: no
	Roles: central
	Roles: peripheral
Advertising Features:
	ActiveInstances: 0x00 (0)
	SupportedInstances: 0x0a (10)
	SupportedIncludes: tx-power
	SupportedIncludes: appearance
	SupportedIncludes: local-name
	SupportedSecondaryChannels: 1M
	SupportedSecondaryChannels: 2M
	SupportedSecondaryChannels: Coded
[bluetooth]# devices
Device 74:45:CE:BA:24:65 WH-CH710N


At this point I started the earbuds (T60) having a problem getting set up.


[CHG] Controller BC:C7:46:9D:25:98 Discoverable: yes
[CHG] Controller BC:C7:46:9D:25:98 Discovering: yes
[NEW] Device 34:95:04:4B:07:3C 34-95-04-4B-07-3C
[CHG] Device 34:95:04:4B:07:3C RSSI: -86
[NEW] Device 0B:20:24:A3:E7:56 T60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -54
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -54
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -54
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -54
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -52
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -56
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -56
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 LegacyPairing: yes
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 LegacyPairing: no
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -64
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -48
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -48
[CHG] Device 0B:20:24:A3:E7:56 LegacyPairing: yes
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -48
[CHG] Device 0B:20:24:A3:E7:56 LegacyPairing: no
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -50
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -50
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -80
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -72
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[bluetooth]# info 0B:20:24:A3:E7:56
Device 0B:20:24:A3:E7:56 (public)
	Name: T60
	Alias: T60
	Class: 0x00240404
	Icon: audio-headset
	Paired: no
	Trusted: no
	Blocked: no
	Connected: no
	LegacyPairing: no
	ManufacturerData Key: 0x7262
	ManufacturerData Value:
  32 32 78 78 11 22 33 44 55 66 aa bb 00 00        22xx."3DUf....  
	RSSI: -46
[DEL] Device 34:95:04:4B:07:3C 34-95-04-4B-07-3C
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -52
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -52
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -58
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -60
[bluetooth]# quit
root@bill:~# rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
root@bill:~# 


Started bluetoothctl again to watch the discovery of the earbuds 0B:20:24:A3:E7:56 T60 and the attempt to get them set up. Setup always fails.


BTW - I have no idea what this is: 
33:EA:17:7C:00:24 33-EA-17-7C-00-24


root@bill:~# bluetoothctl
Agent registered
[CHG] Controller BC:C7:46:9D:25:98 Pairable: yes
[CHG] Controller BC:C7:46:9D:25:98 Discovering: yes
[CHG] Controller BC:C7:46:9D:25:98 Discoverable: yes
[NEW] Device 33:EA:17:7C:00:24 33-EA-17-7C-00-24
[CHG] Device 33:EA:17:7C:00:24 RSSI: -84
[CHG] Controller BC:C7:46:9D:25:98 Discoverable: no
[CHG] Device 33:EA:17:7C:00:24 RSSI is nil
[DEL] Device 33:EA:17:7C:00:24 33-EA-17-7C-00-24
[CHG] Controller BC:C7:46:9D:25:98 Discovering: no
[CHG] Controller BC:C7:46:9D:25:98 Discovering: yes
[CHG] Controller BC:C7:46:9D:25:98 Discoverable: yes
[NEW] Device 33:EA:17:7C:00:24 33-EA-17-7C-00-24
[CHG] Device 33:EA:17:7C:00:24 RSSI: -88
[NEW] Device 0B:20:24:A3:E7:56 T60
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -50
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -48
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -48
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 33:EA:17:7C:00:24 RSSI: -88
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Device 0B:20:24:A3:E7:56 RSSI: -46
[CHG] Controller BC:C7:46:9D:25:98 Discoverable: no
[CHG] Device 33:EA:17:7C:00:24 RSSI is nil
[DEL] Device 33:EA:17:7C:00:24 33-EA-17-7C-00-24
[CHG] Device 0B:20:24:A3:E7:56 RSSI is nil
[CHG] Controller BC:C7:46:9D:25:98 Discovering: no
[CHG] Device 0B:20:24:A3:E7:56 Connected: yes
[T60]# quit
root@bill:~# 


After fixing the verbosity level for bluetooth logging, I see this in the logs:


root@bill:~# journalctl -b0 --grep='0B:20:24:A3:E7:56'
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:24 bill bluetoothd[707]: src/device.c:device_create() dst 0B:20:24:A3:E7:56
Mar 18 08:31:24 bill bluetoothd[707]: src/device.c:device_new() address 0B:20:24:A3:E7:56
Mar 18 08:31:24 bill pulseaudio[1757]: Address: 0B:20:24:A3:E7:56
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0002 eir_len 5
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0002 eir_len 54
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:24 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -60 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -60 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -56 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -56 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -56 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -58 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:device_found_callback() hci0 addr 0B:20:24:A3:E7:56, rssi -60 flags 0x0000 eir_len 54
Mar 18 08:31:25 bill bluetoothd[707]: src/device.c:bonding_request_new() Requesting bonding for 0B:20:24:A3:E7:56
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:adapter_bonding_attempt() hci0 bdaddr 0B:20:24:A3:E7:56 type 0 io_cap 0x01
Mar 18 08:31:25 bill bluetoothd[707]: src/adapter.c:add_accept_list_complete() 0B:20:24:A3:E7:56 added to kernel accept list
Mar 18 08:31:28 bill bluetoothd[707]: src/adapter.c:connected_callback() hci0 device 0B:20:24:A3:E7:56 connected eir_len 10
**Mar 18 08:31:56 bill bluetoothd[707]: src/device.c:create_bond_req_exit() 0B:20:24:A3:E7:56: requestor exited before bonding was completed**
Mar 18 08:31:56 bill bluetoothd[707]: src/adapter.c:adapter_cancel_bonding() hci0 bdaddr 0B:20:24:A3:E7:56 type 0
Mar 18 08:31:56 bill bluetoothd[707]: src/adapter.c:bonding_attempt_complete() hci0 bdaddr 0B:20:24:A3:E7:56 type 0 status 0x10
Mar 18 08:31:56 bill bluetoothd[707]: src/adapter.c:dev_disconnected() Device 0B:20:24:A3:E7:56 disconnected, reason 2
Mar 18 08:31:56 bill bluetoothd[707]: src/adapter.c:bonding_attempt_complete() hci0 bdaddr 0B:20:24:A3:E7:56 type 0 status 0xe
Mar 18 08:31:56 bill bluetoothd[707]: src/adapter.c:remove_accept_list_complete() 0B:20:24:A3:E7:56 removed from kernel accept list
root@bill:~#

---

