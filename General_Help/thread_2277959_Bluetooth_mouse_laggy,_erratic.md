---
title: "Bluetooth mouse laggy, erratic"
date: 2015-05-12
forum: General Help
---

### Post by bach on 2015-05-12
I installed Ubuntu 15.04 (64 bit) on a DELL XPS 13 (model 9343, bios A03) notebook. I use a DELL bluetooth mouse but sometimes it behaves erratically (laggy, jumpy). The problem happens after a few (sometimes one) suspend (to RAM) and resume. Is there a fix for that? I am attaching below some info on my system. Thank you. 

```
cribari@darwin4:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux darwin4 3.19.0-17-generic #17-Ubuntu SMP Wed May 6 16:46:12 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell Device [1028:0019]
	Kernel driver in use: wl
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0c45:670c Microdia 
Bus 001 Device 003: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 0a5c:216f Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.174367] Bluetooth: Core ver 2.20
[    2.174669] Bluetooth: HCI device and connection manager initialized
[    2.174792] Bluetooth: HCI socket layer initialized
[    2.174795] Bluetooth: L2CAP socket layer initialized
[    2.175449] Bluetooth: SCO socket layer initialized
[    2.592936] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
[    3.203438] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
[    3.542418] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.542421] Bluetooth: BNEP filters: protocol multicast
[    3.542425] Bluetooth: BNEP socket layer initialized
[    3.551641] Bluetooth: RFCOMM TTY layer initialized
[    3.551649] Bluetooth: RFCOMM socket layer initialized
[    3.551654] Bluetooth: RFCOMM ver 1.11
[   26.569283] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   26.569287] Bluetooth: HIDP socket layer initialized
[   26.576971] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:11/0005:046D:B00E.0003/input/input15
[   26.577172] hid-generic 0005:046D:B00E.0003: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[   72.448281] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:12/0005:046D:B00E.0004/input/input16
[   72.448526] hid-generic 0005:046D:B00E.0004: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[ 2994.842547] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:13/0005:046D:B00E.0005/input/input17
[ 2994.842810] hid-generic 0005:046D:B00E.0005: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[ 3694.214037] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=1000 lmp_ver=06 lmp_subver=220e
[ 3694.861578] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
[ 3811.777260] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:11/0005:046D:B00E.0006/input/input20
[ 3811.777571] hid-generic 0005:046D:B00E.0006: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[ 5579.876192] Modules linked in: huawei_cdc_ncm cdc_wdm cdc_ncm option usb_wwan usbserial usbnet mii uas usb_storage hid_generic hidp nvram msr binfmt_misc rfcomm bnep nls_iso8859_1 intel_rapl iosf_mbi x86_pkg_temp_thermal dell_wmi sparse_keymap intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul dell_laptop dcdbas btusb crc32_pclmul bluetooth ghash_clmulni_intel hid_multitouch aesni_intel aes_x86_64 lrw uvcvideo gf128mul videobuf2_vmalloc glue_helper wl(POE) videobuf2_memops ablk_helper videobuf2_core cryptd v4l2_common videodev media joydev i915_bpo serio_raw i915 dell_led rtsx_pci_ms intel_ips memstick snd_hda_codec_realtek snd_soc_rt286 snd_hda_codec_generic cfg80211 snd_soc_core drm_kms_helper mei_me lpc_ich shpchp mei snd_compress snd_hda_intel snd_hda_controller drm snd_hda_codec i2c_algo_bit
[ 5579.876223] Workqueue: hci0 hci_power_on [bluetooth]
[ 5579.876261]  [<ffffffffc0e09561>] hci_dev_do_open+0xe1/0xa90 [bluetooth]
[ 5579.876266]  [<ffffffffc0e0a6f0>] hci_power_on+0x40/0x200 [bluetooth]
[ 5579.876284] bluetooth hci0: firmware: brcm/BCM20702A0-0a5c-216f.hcd will not be loaded
[ 5579.876286] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[ 9442.157757] Modules linked in: huawei_cdc_ncm cdc_wdm cdc_ncm option usb_wwan usbserial usbnet mii uas usb_storage hid_generic hidp nvram msr binfmt_misc rfcomm bnep nls_iso8859_1 intel_rapl iosf_mbi x86_pkg_temp_thermal dell_wmi sparse_keymap intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul dell_laptop dcdbas btusb crc32_pclmul bluetooth ghash_clmulni_intel hid_multitouch aesni_intel aes_x86_64 lrw uvcvideo gf128mul videobuf2_vmalloc glue_helper wl(POE) videobuf2_memops ablk_helper videobuf2_core cryptd v4l2_common videodev media joydev i915_bpo serio_raw i915 dell_led rtsx_pci_ms intel_ips memstick snd_hda_codec_realtek snd_soc_rt286 snd_hda_codec_generic cfg80211 snd_soc_core drm_kms_helper mei_me lpc_ich shpchp mei snd_compress snd_hda_intel snd_hda_controller drm snd_hda_codec i2c_algo_bit
[ 9442.157787] Workqueue: hci0 hci_power_on [bluetooth]
[ 9442.157810]  [<ffffffffc0e09561>] hci_dev_do_open+0xe1/0xa90 [bluetooth]
[ 9442.157815]  [<ffffffffc0e0a6f0>] hci_power_on+0x40/0x200 [bluetooth]
[ 9442.157844] bluetooth hci0: firmware: brcm/BCM20702A0-0a5c-216f.hcd will not be loaded
[ 9442.157846] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found
[ 9498.411674] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:11/0005:046D:B00E.0007/input/input25
[ 9498.411880] hid-generic 0005:046D:B00E.0007: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[10589.318323] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:11/0005:046D:B00E.0008/input/input26
[10589.318513] hid-generic 0005:046D:B00E.0008: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[10777.090455] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:11/0005:046D:B00E.0009/input/input27
[10777.090668] hid-generic 0005:046D:B00E.0009: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[10813.977023] input: Dell Travel Mouse WM524 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:11/0005:046D:B00E.000A/input/input28
[10813.977156] hid-generic 0005:046D:B00E.000A: input,hidraw2: BLUETOOTH HID v8.00 Mouse [Dell Travel Mouse WM524] on ac:d1:b8:c0:6f:5c
[10945.835463] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=1000 lmp_ver=06 lmp_subver=220e
[10946.457962] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
[    3.203438] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
[ 3694.861578] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
[ 5579.876160] WARNING: CPU: 2 PID: 6270 at /build/buildd/linux-3.19.0/drivers/base/firmware_class.c:1126 _request_firmware+0x72e/0xbd0()
[ 5579.876238]  [<ffffffff815196ca>] ? _request_firmware+0x5a/0xbd0
[ 5579.876241]  [<ffffffff81519d9e>] _request_firmware+0x72e/0xbd0
[ 5579.876243]  [<ffffffff8151a275>] request_firmware+0x35/0x50
[ 5579.876284] bluetooth hci0: firmware: brcm/BCM20702A0-0a5c-216f.hcd will not be loaded
[ 9442.157726] WARNING: CPU: 3 PID: 9280 at /build/buildd/linux-3.19.0/drivers/base/firmware_class.c:1126 _request_firmware+0x72e/0xbd0()
[ 9442.157798]  [<ffffffff815196ca>] ? _request_firmware+0x5a/0xbd0
[ 9442.157800]  [<ffffffff81519d9e>] _request_firmware+0x72e/0xbd0
[ 9442.157801]  [<ffffffff8151a275>] request_firmware+0x35/0x50
[ 9442.157844] bluetooth hci0: firmware: brcm/BCM20702A0-0a5c-216f.hcd will not be loaded
[10946.457962] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=1624 lmp_ver=06 lmp_subver=220e
bluetooth             491520  23 bnep,hidp,btusb,rfcomm
cribari@darwin4:~$ 

cribari@darwin4:~$ sudo service bluetooth status
[sudo] password for cribari: 
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Ter 2015-05-12 14:21:44 BRT; 2h 48min left
 Main PID: 683 (bluetoothd)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;683 /usr/sbin/bluetoothd -n

Mai 12 11:22:52 darwin4 bluetoothd[683]: Endpoint unregistered: sender=:1.40...e
Mai 12 11:22:52 darwin4 bluetoothd[683]: Endpoint unregistered: sender=:1.40...k
Mai 12 11:22:52 darwin4 bluetoothd[683]: bluetoothd[683]: Endpoint unregiste...G
Mai 12 11:22:52 darwin4 bluetoothd[683]: bluetoothd[683]: Endpoint unregiste...S
Mai 12 11:22:52 darwin4 bluetoothd[683]: bluetoothd[683]: Endpoint unregiste...e
Mai 12 11:22:52 darwin4 bluetoothd[683]: bluetoothd[683]: Endpoint unregiste...k
Mai 12 11:23:18 darwin4 bluetoothd[683]: bluetoothd[683]: Unknown command co...7
Mai 12 11:23:18 darwin4 bluetoothd[683]: Unknown command complete for opcode 37
Mai 12 11:23:23 darwin4 bluetoothd[683]: bluetoothd[683]: Unknown command co...7
Mai 12 11:23:23 darwin4 bluetoothd[683]: Unknown command complete for opcode 37
Hint: Some lines were ellipsized, use -l to show in full.

```

---

### Post by naroyce on 2015-05-13
I'm also now encountering this issue but with an audio sink. Maybe what comes from using vivid-proposed.
Rebooted
Enabled Bluetooth
```
May 13 09:24:44 ubuntu150464 bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/HFPAGMay 13 09:24:44 ubuntu150464 bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/HFPHS
May 13 09:24:44 ubuntu150464 bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/A2DPSource
May 13 09:24:44 ubuntu150464 bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/A2DPSink
May 13 09:24:44 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/HFPAG
May 13 09:24:44 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/HFPHS
May 13 09:24:44 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/A2DPSource
May 13 09:24:44 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Endpoint unregistered: sender=:1.59 path=/MediaEndpoint/BlueZ4/A2DPSink
May 13 09:49:04 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Adapter /org/bluez/851/hci0 has been enabled
May 13 09:49:04 ubuntu150464 bluetoothd[851]: Adapter /org/bluez/851/hci0 has been enabled
```
Search for devices
```
May 13 09:56:37 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Discovery session 0x7fe020e3df20 with :1.121 activated
May 13 09:56:37 ubuntu150464 bluetoothd[851]: Discovery session 0x7fe020e3df20 with :1.121 activated
```
Turn on audio device (Motorola S705 detected)
```
May 13 09:56:45 ubuntu150464 bluetoothd[851]: Unknown command complete for opcode 37
May 13 09:56:45 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Unknown command complete for opcode 37
```
Select audio device and continue
```
May 13 09:57:01 ubuntu150464 bluetoothd[851]: Stopping discovery
May 13 09:57:01 ubuntu150464 bluetoothd[851]: bluetoothd[851]: Stopping discovery
```
Says it succeeded
```
May 13 09:57:45 ubuntu150464 bluetoothd[851]: bluetoothd[851]: 00:02:76:64:A2:CF: error updating services: Connection timed out (110)
May 13 09:57:45 ubuntu150464 bluetoothd[851]: 00:02:76:64:A2:CF: error updating services: Connection timed out (110)
```
It had worked earlier this morning as I was setting up a new system and writing down my procedure but also needing to use Timeshift to rollback mistakes.
I had also wiped bluetooth pairings on both devices and computer.

---

### Post by bach on 2015-05-13
In my case, the problem does not come from vivid-proposed. I was having the problem before I switched to vivid-proposed. The problem happens after a resume and suspend. To make things worse, my notebook oftentimes crashes when I try to suspend to RAM.

---

