---
title: "Dell XPS 8950 Ubuntu 22.04 USB Devices Freezing"
date: 2023-04-13
forum: General Help
---

### Post by prosmart on 2023-04-13
Greetings

Running an XPS 8950 and Ubuntu 22.04 LTS. BIOS is up to date. Kernel is Linux 5.19.0-40-generic x86_64

I  have some kind of issue that is causing my machine to freeze. Intervals between vary  between three times a day and sometime it can go days without happening.  When it does my keyboard and mouse (both USB directly connected)  freeze. 

The system itself is still running - I can see chats changing on  my screen but there is no keyboard, mouse or camera (USB as well).

When I look in /var/log/syslog I see thousands of entries like this below.

```

Apr 13 16:36:37 nigel-xps kernel: [ 2663.336234] xhci_hcd 0000:00:14.0: Frame ID 1434 (reg 11495, index 7) beyond range (1438, 283)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.336240] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.336243] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11495, index 8) beyond range (1438, 283)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.336246] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.336248] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11495, index 9) beyond range (1438, 283)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341276] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341278] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11536, index 10) beyond range (1443, 289)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341279] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341282] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11536, index 11) beyond range (1443, 289)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341284] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341285] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11536, index 12) beyond range (1443, 289)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341287] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341289] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11536, index 13) beyond range (1443, 289)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341290] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341292] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11536, index 14) beyond range (1443, 289)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341293] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341295] xhci_hcd 0000:00:14.0: Frame ID 1435 (reg 11536, index 15) beyond range (1443, 289)
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341296] xhci_hcd 0000:00:14.0: Ignore frame ID field, use SIA bit instead
Apr 13 16:36:37 nigel-xps kernel: [ 2663.341298] xhci_hcd 0000:00:14.0: Frame ID 1436 (reg 11536, index 16) beyond range (1443, 289)
```

lsusb is reporting this:

```

dna@nigel-xps:~/Desktop$ lsusb -tv
/: Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/9p, 20000M/x2
ID 1d6b:0003 Linux Foundation 3.0 root hub
/: Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/16p, 480M
ID 1d6b:0002 Linux Foundation 2.0 root hub
|__ Port 7: Dev 2, If 2, Class=Audio, Driver=snd-usb-audio, 480M
ID 046d:082d Logitech, Inc. HD Pro Webcam C920
|__ Port 7: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
ID 046d:082d Logitech, Inc. HD Pro Webcam C920
|__ Port 7: Dev 2, If 3, Class=Audio, Driver=snd-usb-audio, 480M
ID 046d:082d Logitech, Inc. HD Pro Webcam C920
|__ Port 7: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M
ID 046d:082d Logitech, Inc. HD Pro Webcam C920
|__ Port 8: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
ID 1b1c:1b3c Corsair 
|__ Port 8: Dev 3, If 2, Class=Human Interface Device, Driver=, 12M
ID 1b1c:1b3c Corsair 
|__ Port 8: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
ID 1b1c:1b3c Corsair 
|__ Port 9: Dev 4, If 0, Class=Audio, Driver=snd-usb-audio, 480M
ID 0b05:17f5 ASUSTek Computer, Inc. Xonar U5 sound card
|__ Port 9: Dev 4, If 1, Class=Audio, Driver=snd-usb-audio, 480M
ID 0b05:17f5 ASUSTek Computer, Inc. Xonar U5 sound card
|__ Port 9: Dev 4, If 2, Class=Audio, Driver=snd-usb-audio, 480M
ID 0b05:17f5 ASUSTek Computer, Inc. Xonar U5 sound card
|__ Port 9: Dev 4, If 3, Class=Audio, Driver=snd-usb-audio, 480M
ID 0b05:17f5 ASUSTek Computer, Inc. Xonar U5 sound card
|__ Port 9: Dev 4, If 4, Class=Human Interface Device, Driver=usbhid, 480M
ID 0b05:17f5 ASUSTek Computer, Inc. Xonar U5 sound card
|__ Port 10: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 12M
ID 1b1c:1b3d Corsair Corsair Corsair Gaming K55 RGB Keyboard
|__ Port 10: Dev 5, If 1, Class=Human Interface Device, Driver=usbhid, 12M
ID 1b1c:1b3d Corsair Corsair Corsair Gaming K55 RGB Keyboard
|__ Port 14: Dev 6, If 0, Class=Wireless, Driver=btusb, 12M
ID 8087:0032 Intel Corp. AX210 Bluetooth
|__ Port 14: Dev 6, If 1, Class=Wireless, Driver=btusb, 12M
ID 8087:0032 Intel Corp. AX210 Bluetooth
```

and lspci shows this:

```

00:00.0 Host bridge: Intel Corporation Device 4668 (rev 02)
00:01.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x16 Controller #1 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant (rev 02)
00:06.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 (rev 02)
00:08.0 System peripheral: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator (rev 02)
00:14.0 USB controller: Intel Corporation Device 7ae0 (rev 11)
00:14.2 RAM memory: Intel Corporation Device 7aa7 (rev 11)
00:15.0 Serial bus controller: Intel Corporation Device 7acc (rev 11)
00:15.1 Serial bus controller: Intel Corporation Device 7acd (rev 11)
00:15.2 Serial bus controller: Intel Corporation Device 7ace (rev 11)
00:15.3 Serial bus controller: Intel Corporation Device 7acf (rev 11)
00:16.0 Communication controller: Intel Corporation Device 7ae8 (rev 11)
00:17.0 SATA controller: Intel Corporation Device 7ae2 (rev 11)
00:19.0 Serial bus controller: Intel Corporation Device 7afc (rev 11)
00:19.1 Serial bus controller: Intel Corporation Device 7afd (rev 11)
00:1a.0 PCI bridge: Intel Corporation Device 7ac8 (rev 11)
00:1b.0 PCI bridge: Intel Corporation Device 7ac3 (rev 11)
00:1c.0 PCI bridge: Intel Corporation Device 7abc (rev 11)
00:1c.7 PCI bridge: Intel Corporation Device 7abf (rev 11)
00:1e.0 Communication controller: Intel Corporation Device 7aa8 (rev 11)
00:1f.0 ISA bridge: Intel Corporation Device 7a84 (rev 11)
00:1f.3 Audio device: Intel Corporation Device 7ad0 (rev 11)
00:1f.4 SMBus: Intel Corporation Device 7aa3 (rev 11)
00:1f.5 Serial bus controller: Intel Corporation Device 7aa4 (rev 11)
01:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 XL Upstream Port of PCI Express Switch (rev c5)
02:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 XL Downstream Port of PCI Express Switch
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Navi 22 [Radeon RX 6700/6700 XT / 6800M] (rev c5)
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Navi 21 HDMI Audio [Radeon RX 6800/6800 XT / 6900 XT]
04:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. Device 500f (rev 03)
05:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller PM9A1/PM9A3/980PRO
06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Killer E3000 2.5GbE Controller (rev 06)
08:00.0 Network controller: Intel Corporation Wi-Fi 6 AX210/AX211/AX411 160MHz (rev 1a)
```

Syslog is getting a load of data pumped into it - around 90,000 lines per day.

Anyone have any suggestions where to start looking?

Thanks

Nigel.

---

### Post by prosmart on 2023-04-20
No one? 

Nothing?

---

