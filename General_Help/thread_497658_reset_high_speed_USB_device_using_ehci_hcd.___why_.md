---
title: "reset high speed USB device using ehci_hcd.   why message?"
date: 2007-07-10
forum: General Help
---

### Post by steve457 on 2007-07-10
In my /var/log messages I keep seeing this message come up every minute or so and I am unable to figure out what it is from.  The only USB device I have plugged into my computer is the mouse, and it works fine.  Is there anything else that can cause this message?

Here is the output from /var/log/messages, this pattern seems to continue indefinitely.  My ethernet network connection is on eth1, so I'm not sure what the deal is with the message regarding eth0.

```
Jul 10 09:39:28 localhost kernel: [262154.807471] Unknown OutputIN= OUT=vmnet8 SRC=172.16.51.1 DST=172.16.51.255 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=215 
Jul 10 09:39:28 localhost kernel: [262154.807587] Unknown OutputIN= OUT=vmnet8 SRC=172.16.51.1 DST=172.16.51.255 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=215 
Jul 10 09:39:28 localhost kernel: [262154.807661] Unknown OutputIN= OUT=vmnet1 SRC=172.16.157.1 DST=172.16.157.255 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=215 
Jul 10 09:39:28 localhost kernel: [262154.807723] Unknown OutputIN= OUT=vmnet1 SRC=172.16.157.1 DST=172.16.157.255 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=215 
Jul 10 09:39:28 localhost kernel: [262154.807793] Unknown OutputIN= OUT=eth0 SRC=169.254.9.50 DST=169.254.255.255 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=215 
Jul 10 09:39:28 localhost kernel: [262154.807852] Unknown OutputIN= OUT=eth0 SRC=169.254.9.50 DST=169.254.255.255 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=215 
Jul 10 09:39:41 localhost kernel: [262167.427375] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:41:20 localhost kernel: [262266.104767] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:43:25 localhost kernel: [262390.867613] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:43:42 localhost kernel: [262408.314631] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:43:55 localhost kernel: [262421.409586] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:45:01 localhost kernel: [262486.922668] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:47:39 localhost kernel: [262644.610426] usb 7-1: reset high speed USB device using ehci_hcd and address 2
Jul 10 09:51:22 localhost kernel: [262867.224231] usb 7-1: reset high speed USB device using ehci_hcd and address 2
```

Here's the output from lspci

```
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1c.5 PCI bridge: Intel Corporation Unknown device 294a (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
02:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6121 (rev b1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8052 PCI-E ASF Gigabit Ethernet Controller (rev 21)
05:00.0 PCI bridge: NEC Corporation uPD720400 PCI Express - PCI/PCI-X Bridge (rev 06)
05:00.1 PCI bridge: NEC Corporation uPD720400 PCI Express - PCI/PCI-X Bridge (rev 06)
09:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
```


Are there any other log files that would help in trying to determine what is causing these messages?

Thanks.

---

### Post by Who on 2007-07-17
I'm getting the same string of messages - any help from anyone would be appreciated:

Clarification:

I'm transferring data between two USB hard disks. It is very slow - they should both be USB2. 1 is a freecom disk - the other my SATA disk in a cheap caddy. SATA disk has multiple partitions

my  dmesg is stuffed with this line, over and over again.

[13535.919113] usb 2-5: reset high speed USB device using ehci_hcd and address 3

And here is what looked relevant from earlier on
[  406.374859] usb 2-5: new high speed USB device using ehci_hcd and address 3
[  406.508701] usb 2-5: configuration #1 chosen from 1 choice
[  406.843558] usbcore: registered new interface driver libusual
[  406.856127] Initializing USB Mass Storage driver...
[  406.856253] scsi3 : SCSI emulation for USB Mass Storage devices
[  406.856320] usb-storage: device found at 3
[  406.856322] usb-storage: waiting for device to settle before scanning
[  406.856334] usbcore: registered new interface driver usb-storage
[  406.856337] USB Mass Storage support registered.
[  411.850666] usb-storage: device scan complete
[  411.851417] scsi 3:0:0:0: Direct-Access     Maxtor 7 L250S0           1G20 PQ: 0 ANSI: 2 CCS
[  411.942371] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[  411.943442] sda: Write Protect is off
[  411.943446] sda: Mode Sense: 00 38 00 00
[  411.943449] sda: assuming drive cache: write through
[  411.944940] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[  411.945815] sda: Write Protect is off
[  411.945819] sda: Mode Sense: 00 38 00 00
[  411.945821] sda: assuming drive cache: write through
[  411.946323]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 >
[  412.126584] sd 3:0:0:0: Attached scsi disk sda
[  412.139163] sd 3:0:0:0: Attached scsi generic sg0 type 0
[  412.939583] kjournald starting.  Commit interval 5 seconds
[  412.939701] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  412.940663] EXT3 FS on sda5, internal journal
[  412.940759] EXT3-fs: mounted filesystem with ordered data mode.
[  413.107536] kjournald starting.  Commit interval 5 seconds
[  413.165383] EXT3 FS on sda1, internal journal
[  413.165480] EXT3-fs: mounted filesystem with ordered data mode.
[  413.876927] ReiserFS: sda9: found reiserfs format "3.6" with standard journal
[  413.877084] ReiserFS: sda9: using ordered data mode
[  413.899072] ReiserFS: sda9: journal params: device sda9, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  413.900869] ReiserFS: sda9: checking transaction log (sda9)
[  414.108663] ReiserFS: sda9: Using r5 hash to sort names
[  414.306425] kjournald starting.  Commit interval 5 seconds
[  414.308734] EXT3 FS on sda10, internal journal
[  414.310332] EXT3-fs: mounted filesystem with ordered data mode.
[  414.468759] kjournald starting.  Commit interval 5 seconds
[  414.472975] EXT3 FS on sda6, internal journal
[  414.473082] EXT3-fs: mounted filesystem with ordered data mode.
[  414.559901] kjournald starting.  Commit interval 5 seconds
[  414.560643] EXT3 FS on sda7, internal journal
[  414.560726] EXT3-fs: mounted filesystem with ordered data mode.
[  414.766915] kjournald starting.  Commit interval 5 seconds
[  414.772058] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  414.933482] EXT3 FS on sda13, internal journal
[  414.933580] EXT3-fs: mounted filesystem with ordered data mode.
[  416.897025] kjournald starting.  Commit interval 5 seconds
[  416.897914] EXT3 FS on sda12, internal journal
[  416.898004] EXT3-fs: mounted filesystem with ordered data mode.
[  454.959822] usb 2-5: reset high speed USB device using ehci_hcd and address 3

---

