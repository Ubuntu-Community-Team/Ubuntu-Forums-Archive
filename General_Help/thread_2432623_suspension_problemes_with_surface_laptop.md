---
title: "suspension problemes with surface laptop"
date: 2019-12-05
forum: General Help
---

### Post by alektheos on 2019-12-05
I have recently installed ubuntu 18.04 in my surface laptop with [this]("https://github.com/jakeday/linux-surface") linux kernel for hardware support but suspension isn't working: the computer suspends for some seconds or sometimes for some minutes but it exits suspension without reason (even with the systemctl suspend or pm-suspend commands). I've been looking for solutions for a week without result. I found some threads about this saying that to know what is causing the problem we have to use the dmesg command but I don't know what is the problem nor where to find it. here is the display of dmesg after a suspension
```
[ 8090.839456] mwifiex_pcie 0000:02:00.0: info: successfully disconnected from 78:32:1b:2d:8a:9c: reason code 3
[ 8090.839511] mwifiex_pcie 0000:02:00.0: wlp2s0: already connected
[ 8090.875992] IPTS ipts_mei_cl_exit() is called
[ 8090.997567] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: error in reading m2h msg
[ 8090.997581] IPTS removed
[ 8091.078023] mwifiex_pcie 0000:02:00.0: info: shutdown mwifiex...
[ 8091.079840] mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
[ 8091.200695] PM: suspend entry (s2idle)
[ 8091.200696] PM: Syncing filesystems ... done.
[ 8091.215469] Freezing user space processes ... (elapsed 0.001 seconds) done.
[ 8091.217236] OOM killer disabled.
[ 8091.217236] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 8091.218488] printk: Suspending console(s) (use no_console_suspend to debug)
[ 8091.713989] [drm] HuC: Loaded firmware i915/kbl_huc_ver02_00_1810.bin (version 2.0)
[ 8091.719517] [drm] GuC: Loaded firmware i915/kbl_guc_ver9_39.bin (version 9.39)
[ 8091.719685] i915 0000:00:02.0: GuC firmware version 9.39
[ 8091.719688] i915 0000:00:02.0: GuC submission enabled
[ 8091.719691] i915 0000:00:02.0: HuC enabled
[ 8091.732947] ipts: initializing ipts
[ 8091.733397] ipts: Intel iTouch framework initialized
[ 8091.788571] Restarting kernel threads ... done.
[ 8091.789282] PM: PM: Sleeping for 3000 milliseconds.
[ 8091.931681] nvme nvme0: 2/0/0 default/read/poll queues
[ 8094.913280] OOM killer enabled.
[ 8094.913283] Restarting tasks ... done.
[ 8094.938530] PM: suspend exit
[ 8094.955851] IPTS ipts_mei_cl_init() is called
[ 8094.971623] probing Intel Precise Touch & Stylus
[ 8094.971624] IPTS using DMA_BIT_MASK(64)
[ 8094.999374] input: ipts 1B96:0979 UNKNOWN as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0006/input/input36
[ 8094.999584] input: ipts 1B96:0979 as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0006/input/input38
[ 8094.999702] input: ipts 1B96:0979 Touchscreen as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0006/input/input39
[ 8094.999808] input: ipts 1B96:0979 Mouse as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0006/input/input40
[ 8094.999933] hid-multitouch 0044:1B96:0979.0006: input,hidraw0: <UNKNOWN> HID v1bd00.05 Mouse [ipts 1B96:0979] on heci3
[ 8095.011625] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: touch enabled 4
[ 8095.025765] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[ 8095.026052] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[ 8095.042141] mwifiex_pcie: try set_consistent_dma_mask(32)
[ 8095.042238] mwifiex_pcie: PCI memory map Virt0: 00000000e9ff65f8 PCI memory map Virt2: 00000000999c6b22
[ 8095.047450] mwifiex_pcie 0000:02:00.0: WLAN FW already running! Skip FW dnld
[ 8095.047452] mwifiex_pcie 0000:02:00.0: WLAN FW is active
[ 8095.137292] mwifiex_pcie 0000:02:00.0: info: MWIFIEX VERSION: mwifiex 1.0 (15.68.7.p154) 
[ 8095.137293] mwifiex_pcie 0000:02:00.0: driver_version = mwifiex 1.0 (15.68.7.p154) 
[ 8095.140070] mwifiex_pcie 0000:02:00.0 wlp2s0: renamed from mlan0
[ 8099.342662] mwifiex_pcie 0000:02:00.0: info: trying to associate to 'Midway' bssid 78:32:1b:2d:8a:9c
[ 8099.389361] mwifiex_pcie 0000:02:00.0: info: associated to bssid 78:32:1b:2d:8a:9c successfully
[ 8099.425396] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 8247.787677] Bluetooth: hci0: advertising data len corrected
[ 8248.162599] Bluetooth: hci0: advertising data len corrected
[ 8249.037724] Bluetooth: hci0: advertising data len corrected
[ 8249.664103] Bluetooth: hci0: advertising data len corrected
[ 8346.906644] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: touch enabled 4
[ 8422.055569] mwifiex_pcie 0000:02:00.0: info: successfully disconnected from 78:32:1b:2d:8a:9c: reason code 0
[ 8468.149479] mwifiex_pcie 0000:02:00.0: info: trying to associate to 'Midway' bssid 78:32:1b:2d:8a:9c
[ 8468.456529] mwifiex_pcie 0000:02:00.0: info: associated to bssid 78:32:1b:2d:8a:9c successfully
[ 8468.496994] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 8681.535772] perf: interrupt took too long (3266 > 3245), lowering kernel.perf_event_max_sample_rate to 61000
[ 9514.969193] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: touch enabled 4
[ 9574.152335] [drm] Reducing the compressed framebuffer size. This may lead to less power savings than a non-reduced-size. Try to increase stolen memory size if available in BIOS.
[ 9574.163118] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: touch enabled 4
[10028.065397] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: touch enabled 4
[11027.748070] mwifiex_pcie 0000:02:00.0: info: successfully disconnected from 78:32:1b:2d:8a:9c: reason code 3
[11027.748203] mwifiex_pcie 0000:02:00.0: wlp2s0: already connected
[11027.844394] IPTS ipts_mei_cl_exit() is called
[11027.985330] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: error in reading m2h msg
[11027.985438] IPTS removed
[11028.075502] mwifiex_pcie 0000:02:00.0: info: shutdown mwifiex...
[11028.075688] mwifiex_pcie 0000:02:00.0: PREP_CMD: card is removed
[11028.202558] PM: suspend entry (s2idle)
[11028.202559] PM: Syncing filesystems ... done.
[11028.233047] Freezing user space processes ... (elapsed 0.015 seconds) done.
[11028.248975] OOM killer disabled.
[11028.248976] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[11028.250477] printk: Suspending console(s) (use no_console_suspend to debug)
[11464.673885] [drm] HuC: Loaded firmware i915/kbl_huc_ver02_00_1810.bin (version 2.0)
[11464.679663] [drm] GuC: Loaded firmware i915/kbl_guc_ver9_39.bin (version 9.39)
[11464.679818] i915 0000:00:02.0: GuC firmware version 9.39
[11464.679820] i915 0000:00:02.0: GuC submission enabled
[11464.679821] i915 0000:00:02.0: HuC enabled
[11464.689655] ipts: initializing ipts
[11464.689961] ipts: Intel iTouch framework initialized
[11464.748723] Restarting kernel threads ... done.
[11464.749015] PM: PM: Sleeping for 3000 milliseconds.
[11464.894307] nvme nvme0: 2/0/0 default/read/poll queues
[11467.806237] OOM killer enabled.
[11467.806241] Restarting tasks ... done.
[11467.828114] PM: suspend exit
[11467.856884] IPTS ipts_mei_cl_init() is called
[11467.867473] probing Intel Precise Touch & Stylus
[11467.867474] IPTS using DMA_BIT_MASK(64)
[11467.880836] input: ipts 1B96:0979 UNKNOWN as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0007/input/input46
[11467.881593] input: ipts 1B96:0979 as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0007/input/input48
[11467.881671] input: ipts 1B96:0979 Touchscreen as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0007/input/input49
[11467.882024] input: ipts 1B96:0979 Mouse as /devices/pci0000:00/0000:00:16.4/mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F/0044:1B96:0979.0007/input/input50
[11467.882121] hid-multitouch 0044:1B96:0979.0007: input,hidraw0: <UNKNOWN> HID v1bd00.05 Mouse [ipts 1B96:0979] on heci3
[11467.896475] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[11467.896654] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[11467.908196] mwifiex_pcie: try set_consistent_dma_mask(32)
[11467.908250] mwifiex_pcie: PCI memory map Virt0: 00000000377449c1 PCI memory map Virt2: 00000000b0abd656
[11467.914872] mwifiex_pcie 0000:02:00.0: WLAN FW already running! Skip FW dnld
[11467.914874] mwifiex_pcie 0000:02:00.0: WLAN FW is active
[11468.020798] mwifiex_pcie 0000:02:00.0: info: MWIFIEX VERSION: mwifiex 1.0 (15.68.7.p154) 
[11468.020799] mwifiex_pcie 0000:02:00.0: driver_version = mwifiex 1.0 (15.68.7.p154) 
[11468.023539] mwifiex_pcie 0000:02:00.0 wlp2s0: renamed from mlan0
[11468.051663] [drm] Reducing the compressed framebuffer size. This may lead to less power savings than a non-reduced-size. Try to increase stolen memory size if available in BIOS.
[11468.149491] ipts mei::3e8d0870-271a-4208-8eb5-9acb9402ae04:0F: touch enabled 4
[11472.266527] mwifiex_pcie 0000:02:00.0: info: trying to associate to 'Midway' bssid 78:32:1b:2d:8a:9c
[11472.309101] mwifiex_pcie 0000:02:00.0: info: associated to bssid 78:32:1b:2d:8a:9c successfully
[11472.348605] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

```
thank you in advance for any reply

---

