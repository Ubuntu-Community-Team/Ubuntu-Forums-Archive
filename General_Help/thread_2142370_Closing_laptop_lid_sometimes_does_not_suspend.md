---
title: "Closing laptop lid *sometimes* does not suspend"
date: 2013-05-05
forum: General Help
---

### Post by sona1111 on 2013-05-05
After upgrading to 12.10 If I close the lid to my laptop sometimes it will not suspend. (it always resumes correctly) Someone suggested closing each program to see if one was causing the problem. I did this and found even with then all closed it still did not work. The screen always turns off so I know the switch is working. 

Dmesg after a failed suspend:

```
[66358.180115] usb 5-1: new full-speed USB device number 4 using uhci_hcd[66358.345447] usb 5-1: New USB device found, idVendor=0a5c, idProduct=2110
[66358.345454] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[66358.345458] usb 5-1: Product: BCM2045B
[66358.345461] usb 5-1: Manufacturer: Broadcom Corp
[66360.548127] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66365.548340] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66374.159261] hid-generic 0005:17EF:6002.0009: unknown main item tag 0x0
[66374.173755] input: ThinkPad Bluetooth Laser Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input16
[66374.174018] hid-generic 0005:17EF:6002.0009: input,hidraw0: BLUETOOTH HID v2.45 Mouse [ThinkPad Bluetooth Laser Mouse] on 00:16:CF:DD:D5:2E
[66406.442522] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[66406.560715] eth1:  setting half-duplex.
[66406.561330] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[66406.834262] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[66408.956623] wlan0: authenticate with 00:13:10:07:75:73
[66408.956739] wlan0: send auth to 00:13:10:07:75:73 (try 1/3)
[66408.958587] wlan0: authenticated
[66408.960079] wlan0: associate with 00:13:10:07:75:73 (try 1/3)
[66408.962345] wlan0: RX AssocResp from 00:13:10:07:75:73 (capab=0x411 status=0 aid=3)
[66408.963724] wlan0: associated
[66408.964110] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[66562.940396] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66567.940108] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66617.506007] hid-generic 0005:17EF:6002.000A: unknown main item tag 0x0
[66617.524171] input: ThinkPad Bluetooth Laser Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input17
[66617.524797] hid-generic 0005:17EF:6002.000A: input,hidraw0: BLUETOOTH HID v2.45 Mouse [ThinkPad Bluetooth Laser Mouse] on 00:16:CF:DD:D5:2E
[66695.605532] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66695.605557] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66886.046130] hid-generic 0005:17EF:6002.000B: unknown main item tag 0x0
[66886.055527] input: ThinkPad Bluetooth Laser Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input18
[66886.055884] hid-generic 0005:17EF:6002.000B: input,hidraw0: BLUETOOTH HID v2.45 Mouse [ThinkPad Bluetooth Laser Mouse] on 00:16:CF:DD:D5:2E

```

And another try:

```
rt `capacity' property: 4294967291[66617.506007] hid-generic 0005:17EF:6002.000A: unknown main item tag 0x0
[66617.524171] input: ThinkPad Bluetooth Laser Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input17
[66617.524797] hid-generic 0005:17EF:6002.000A: input,hidraw0: BLUETOOTH HID v2.45 Mouse [ThinkPad Bluetooth Laser Mouse] on 00:16:CF:DD:D5:2E
[66695.605532] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66695.605557] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[66886.046130] hid-generic 0005:17EF:6002.000B: unknown main item tag 0x0
[66886.055527] input: ThinkPad Bluetooth Laser Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input18
[66886.055884] hid-generic 0005:17EF:6002.000B: input,hidraw0: BLUETOOTH HID v2.45 Mouse [ThinkPad Bluetooth Laser Mouse] on 00:16:CF:DD:D5:2E
[68680.707292] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
[68680.707402] wlan0: deauthenticating from 00:13:10:07:75:73 by local choice (reason=3)
[68680.707447] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.707455] iwl3945 0000:03:00.0: Error sending C_REM_STA: enqueue_hcmd failed: -5
[68680.707463] iwl3945 0000:03:00.0: Error removing station 00:13:10:07:75:73
[68680.712153] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.712164] iwl3945 0000:03:00.0: Error sending C_QOS_PARAM: enqueue_hcmd failed: -5
[68680.712174] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.712180] iwl3945 0000:03:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[68680.712187] iwl3945 0000:03:00.0: Error setting new configuration (-5).
[68680.712194] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.712200] iwl3945 0000:03:00.0: Error sending C_RXON_ASSOC: enqueue_hcmd failed: -5
[68680.728170] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.728183] iwl3945 0000:03:00.0: Error sending C_RXON_ASSOC: enqueue_hcmd failed: -5
[68680.728195] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.728201] iwl3945 0000:03:00.0: Error sending C_LEDS: enqueue_hcmd failed: -5
[68680.728213] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.728219] iwl3945 0000:03:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[68680.728226] iwl3945 0000:03:00.0: Error setting new configuration (-5).
[68680.732337] cfg80211: All devices are disconnected, going to restore regulatory settings
[68680.732343] cfg80211: Restoring regulatory settings
[68680.732350] cfg80211: Calling CRDA to update world regulatory domain
[68680.738682] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[68680.738689] cfg80211: World regulatory domain updated:
[68680.738692] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[68680.738695] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[68680.738698] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[68680.738701] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[68680.738704] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[68680.738707] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[68680.740728] iwl3945 0000:03:00.0: Not sending command - RF KILL
[68680.740734] iwl3945 0000:03:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[68680.740739] iwl3945 0000:03:00.0: Error setting new configuration (-5).
[68680.744013] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[68680.792188] usb 5-1: USB disconnect, device number 4
[68681.160305] eth1:  setting half-duplex.
[68681.160856] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[68685.752037] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291
[68690.752086] power_supply hid-00:02:76:35:11:76-battery: driver failed to report `capacity' property: 4294967291

```

---

### Post by sona1111 on 2013-05-07
This is still a problem.

---

