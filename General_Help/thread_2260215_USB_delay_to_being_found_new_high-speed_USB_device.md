---
title: "USB delay to being found: new high-speed USB device number 116 using ehci-pci"
date: 2015-01-10
forum: General Help
---

### Post by samuelsimon on 2015-01-10
I have a ZyXEL G-202 USB wifi dongle which is attached to my ubuntu 14.10 system. On startup I would exepect it to be found and then connect to the wifi. Instead I get a "new high-speed USB device number 116 using ehci-pci" message in dmesg repeated (with the number changing)  for many minutes:

```
[ 1081.344055] usb 1-1: new high-speed USB device number 116 using ehci-pci
[ 1083.196039] usb 1-1: new high-speed USB device number 124 using ehci-pci
[ 1083.968037] usb 1-1: new high-speed USB device number 127 using ehci-pci
```

then when it finally connects I get:

```
[ 1085.156042] usb 3-1: new full-speed USB device number 3 using uhci_hcd
[ 1085.301059] usb 3-1: not running at top speed; connect to a high speed hub
[ 1085.329062] usb 3-1: New USB device found, idVendor=0586, idProduct=3410
[ 1085.329068] usb 3-1: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[ 1085.329073] usb 3-1: Product: ZyXEL G-202
[ 1085.329078] usb 3-1: Manufacturer: ZyDAS
[ 1085.355214] cfg80211: Calling CRDA to update world regulatory domain
[ 1085.363304] cfg80211: World regulatory domain updated:
[ 1085.363309] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1085.363311] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1085.363314] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1085.363316] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1085.363318] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1085.363320] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1085.484043] usb 3-1: reset full-speed USB device number 3 using uhci_hcd
[ 1085.847521] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 1085.847895] zd1211rw 3-1:1.0: phy0
[ 1085.847933] usbcore: registered new interface driver zd1211rw
[ 1085.949061] zd1211rw 3-1:1.0: firmware version 4725
[ 1086.009062] zd1211rw 3-1:1.0: zd1211b chip 0586:3410 v4810 full 00-13-49 AL2230_RF pa0 g---S
[ 1086.066108] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1086.066151] cfg80211: Calling CRDA for country: DE
[ 1086.067869] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1086.070666] cfg80211: Regulatory domain changed to country: DE
[ 1086.070673] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1086.070677] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1086.070681] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1086.070685] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1086.070689] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[ 1086.070693] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[ 1088.184614] wlan0: authenticate with 5c:7d:5e:cc:0a:c6
[ 1088.245173] wlan0: send auth to 5c:7d:5e:cc:0a:c6 (try 1/3)
[ 1088.248103] wlan0: authenticated
[ 1088.252028] wlan0: associate with 5c:7d:5e:cc:0a:c6 (try 1/3)
[ 1088.261104] wlan0: RX AssocResp from 5c:7d:5e:cc:0a:c6 (capab=0x411 status=0 aid=7)
[ 1088.262064] wlan0: associated
[ 1088.262101] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1088.298136] wlan0: deauthenticating from 5c:7d:5e:cc:0a:c6 by local choice (reason=2)
[ 1088.319138] wlan0: authenticate with 5c:7d:5e:cc:0a:c6
[ 1088.339159] wlan0: send auth to 5c:7d using ehci-pci
[ 1083.196039] usb 1-1: new high-speed USB device number 1:5e:cc:0a:c6 (try 1/3)
[ 1088.339388] cfg80211: Calling CRDA to update world regulatory domain
[ 1088.344294] cfg80211: World regulatory domain updated:
[ 1088.344301] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1088.344305] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1088.344310] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1088.344314] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1088.344317] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1088.344321] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1089.449132] wlan0: send auth to 5c:7d:5e:cc:0a:c6 (try 2/3)
[ 1089.452125] wlan0: authenticated
[ 1089.456039] wlan0: associate with 5c:7d:5e:cc:0a:c6 (try 1/3)
[ 1089.660023] wlan0: associate with 5c:7d:5e:cc:0a:c6 (try 2/3)
[ 1089.670104] wlan0: RX AssocResp from 5c:7d:5e:cc:0a:c6 (capab=0x411 status=0 aid=7)
[ 1089.671066] wlan0: associated
```

My guess is that it is trying to connect to "high-speed" but needs to connect to "full-speed". Or "ehci-pci" when it needs "uhci_hcd".

Any suggestions if this is likley to be the case and how I can force it to default to "full-speed" and/or "uhci_hcd"? Any other suggestions on what may be the problem or how I can solve it would be apprecaited.

Thanks

---

