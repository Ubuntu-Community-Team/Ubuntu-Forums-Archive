---
title: "External HDD Problem"
date: 2013-12-13
forum: General Help
---

### Post by timfinley on 2013-12-13
I have an external HDD that weighs in at 3 TBs and connects to my Ubuntu 13.04 64-bit machine. It connected all well and good, the last time I plugged it in. Now it doesn't work so well. When I plug it in to m usb 3.0 port, I get nothing, as if it never existed and I see this when I punch in dsmeg:

```
[75228.652034] usb 3-1: new high-speed USB device number 2 using xhci_hcd[75228.701199] usb 3-1: New USB device found, idVendor=0480, idProduct=d010
[75228.701211] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[75228.701217] usb 3-1: Product: External USB 3.0
[75228.701222] usb 3-1: Manufacturer: Toshiba
[75228.701227] usb 3-1: SerialNumber: *****EDITED******
[75229.499752] Initializing USB Mass Storage driver...
[75229.499966] scsi5 : usb-storage 3-1:1.0
[75229.500093] usbcore: registered new interface driver usb-storage
[75229.500096] USB Mass Storage support registered.
[75238.526531] scsi 5:0:0:0: Direct-Access     Toshiba  External USB 3.0 0201 PQ: 0 ANSI: 6
[75238.528032] sd 5:0:0:0: Attached scsi generic sg2 type 0
[75238.531138] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[75238.552454] sd 5:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[75238.552951] sd 5:0:0:0: [sdb] Write Protect is off
[75238.552962] sd 5:0:0:0: [sdb] Mode Sense: 2b 00 00 00
[75238.553366] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[75238.555617] sd 5:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[75238.590538]  sdb: sdb1
[75238.594053] sd 5:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[75238.594627] sd 5:0:0:0: [sdb] Attached SCSI disk
[75800.511628] usb 3-1: USB disconnect, device number 2
[75854.675740] usb 1-1.2: USB disconnect, device number 3
```

It works, if only slightly when I use usb 2.0 here is the dsmeg from it:

```
[79981.224718] usb 3-1: new high-speed USB device number 3 using xhci_hcd
[79981.273973] usb 3-1: New USB device found, idVendor=0480, idProduct=d010
[79981.273984] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[79981.273990] usb 3-1: Product: External USB 3.0
[79981.273995] usb 3-1: Manufacturer: Toshiba
[79981.274000] usb 3-1: SerialNumber: ****EDITED****
[79981.275376] scsi6 : usb-storage 3-1:1.0
[79991.192741] scsi 6:0:0:0: Direct-Access     Toshiba  External USB 3.0 0201 PQ: 0 ANSI: 6
[79991.194828] sd 6:0:0:0: Attached scsi generic sg2 type 0
[79991.199187] sd 6:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[79991.228834] sd 6:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[79991.229348] sd 6:0:0:0: [sdb] Write Protect is off
[79991.229359] sd 6:0:0:0: [sdb] Mode Sense: 2b 00 00 00
[79991.229770] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[79991.231655] sd 6:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[79991.267004]  sdb: sdb1
[79991.270635] sd 6:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[79991.273856] sd 6:0:0:0: [sdb] Attached SCSI disk
```

And that works, but it is *Very* slow. Ideas? Suggestions? I feel like the problem lies within the "Very big device" message, but i'm not that proficient yet...

---

### Post by nerdtron on 2013-12-13
What is the filesystem of the external drive?
Did you safely removed/eject it properly since you last used it?
Does windows (if you have windows) recognize the drive?

---

### Post by timfinley on 2013-12-13
The file system is ntfs, Yes I safely removed it. No, I don't have a windows computer at all. I can try my ps3 but I read somewhere that ps3's can't read ntfs? It works when I use my usb 2.0 port but not the 3.0. Which is strange because it used to work with the 3.0....

---

### Post by steven0brock on 2013-12-13
I had somewhat of a similar issue with a couple 500GB external hdd's.
I had to edit the 80-udisks.rules located in /lib/udev/rules.d

[COLOR=#000000]Must comment these lins out in 80-udisks.rules:[/COLOR]

[COLOR=#000000]################################################## ################################################## ##########[/COLOR]


[COLOR=#000000]# Check if a disk is ATA SMART capable[/COLOR]
[COLOR=#000000]#[/COLOR]


[COLOR=#000000]# USB ATA enclosures with a SAT layer[/COLOR]
[COLOR=#000000]# KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="usb", ENV{DEVTYPE}=="disk", IMPORT{program}="udisks-probe-ata-smart $tempnode"[/COLOR]


[COLOR=#000000]# ATA disks driven by libata[/COLOR]
[COLOR=#000000]# KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="udisks-probe-ata-smart $tempnode"[/COLOR]


[COLOR=#000000]# ATA disks connected via SAS (not driven by libata)[/COLOR]
[COLOR=#000000]# KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="scsi", ENV{DEVTYPE}=="disk", ENV{ID_VENDOR}=="ATA", IMPORT{program}="udisks-probe-ata-smart $tempnode"[/COLOR]

---

