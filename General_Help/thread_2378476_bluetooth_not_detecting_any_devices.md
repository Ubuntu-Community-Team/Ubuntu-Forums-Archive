---
title: "bluetooth not detecting any devices"
date: 2017-11-23
forum: General Help
---

### Post by 123systemshah on 2017-11-23
```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
    Kernel driver in use: wl
--
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Sony Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [104d:90b8]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b3aa Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 0489:e062 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0781:5590 SanDisk Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 019: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 018: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: B8:76:3F:B2:17:82  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN INQUIRY 
    RX bytes:4473 acl:0 sco:0 events:613 errors:0
    TX bytes:4425 acl:0 sco:0 commands:526 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'shekhar-ss'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)

[   10.611840] Bluetooth: Core ver 2.22
[   10.611861] Bluetooth: HCI device and connection manager initialized
[   10.611864] Bluetooth: HCI socket layer initialized
[   10.611867] Bluetooth: L2CAP socket layer initialized
[   10.611871] Bluetooth: SCO socket layer initialized
[   10.742381] Bluetooth: hci0: BCM: chip id 70
[   10.758386] Bluetooth: hci0: shekhar-ss
[   10.758390] Bluetooth: hci0: BCM (001.001.011) build 0000
[   10.818629] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   10.818634] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   12.844103] Bluetooth: hci0 command 0x1003 tx timeout
[   14.481386] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.481387] Bluetooth: BNEP filters: protocol multicast
[   14.481391] Bluetooth: BNEP socket layer initialized
[   26.503565] Bluetooth: RFCOMM TTY layer initialized
[   26.503572] Bluetooth: RFCOMM socket layer initialized
[   26.503579] Bluetooth: RFCOMM ver 1.11
[131514.175112] Modules linked in: nls_iso8859_1 binfmt_misc rfcomm bnep intel_rapl x86_pkg_temp_thermal intel_powerclamp uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev coretemp media btusb btrtl btbcm btintel bluetooth rndis_host snd_hda_codec_hdmi cdc_ether usbnet kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel wl(POE) snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel cryptd intel_cstate snd_hda_codec snd_hda_core snd_hwdep intel_rapl_perf snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi joydev rtsx_pci_ms lpc_ich memstick cfg80211 input_leds serio_raw snd_seq snd_seq_device snd_timer snd mei_me mei shpchp mac_hid soundcore sony_laptop parport_pc ppdev lp parport autofs4 hid_generic usbhid hid uas usb_storage i915 rtsx_pci_sdmmc
[163268.045331] Bluetooth: hci0: BCM: chip id 70
[163268.061339] Bluetooth: hci0: shekhar-ss
[163268.061345] Bluetooth: hci0: BCM (001.001.011) build 0000
[163268.073743] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[163268.073748] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[163270.090712] Bluetooth: hci0 command 0x1003 tx timeout
```

---

### Post by jeremy31 on 2017-11-23
```
wget https://www.dropbox.com/s/prxmhz1zvt0chdc/fw-0489_e062.hcd
```
```
sudo cp /fw-0489_e062.hcd /lib/firmware/brcm/BCM.hcd
```
Reboot and it should function

---

