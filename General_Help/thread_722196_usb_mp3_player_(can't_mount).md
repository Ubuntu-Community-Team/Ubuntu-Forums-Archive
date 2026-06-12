---
title: "usb mp3 player (can't mount)"
date: 2008-03-12
forum: General Help
---

### Post by ieshmutis on 2008-03-12
Hey, I just migrated to linux from windows and the only thing why I keep windows because of my usb mp3 player which doesn't mount on ubuntu 7.10 I tried to mount it manualy with <mount -t vfat /dev/sda1 /media/usb> terminal outputs me "mount: special device /dev/sda1 does not exist" ..my friends usb mp3 player auto mounts perfectly. Please help me to fix it

dmesg | tail

[ 4576.970261] sd 205:0:0:1: [sda] Write Protect is off
[ 4576.970269] sd 205:0:0:1: [sda] Mode Sense: 00 00 00 00
[ 4576.970273] sd 205:0:0:1: [sda] Assuming drive cache: write through
[ 4576.970369] sd 205:0:0:1: [sda] Attached SCSI removable disk
[ 4576.970430] sd 205:0:0:1: Attached scsi generic sg1 type 0
[ 4578.899838] usb 1-3: new full speed USB device using ohci_hcd and address 81
[ 4579.112998] usb 1-3: configuration #1 chosen from 1 choice
[ 4579.116039] scsi206 : SCSI emulation for USB Mass Storage devices
[ 4579.116243] usb-storage: device found at 81
[ 4579.116245] usb-storage: waiting for device to settle before scanning

fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9d50

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3572    28692058+   c  W95 FAT32 (LBA)
/dev/hda2            3573        7098    28322595   1c  Hidden W95 FAT32 (LBA)
/dev/hda3            7099        7130      257040   82  Linux swap / Solaris
/dev/hda4            7131       10011    23141632+  83  Linux

---

### Post by Gen2ly on 2008-03-12
have you tried /dev/usb?  See if the devicenode is being spawned.

---

### Post by ieshmutis on 2008-03-12
there is file lp0 in /dev/usb/ and if I try to mount /dev/usb - "mount: /dev/usb is not a block device" hmm also i noticed 3 files that appears in /dev/ and dissappears in about second interval. usbdev1.xxx_ep00, usbdev1.xxx_ep01, usbdev1.xxx_ep82 (xxx changes every time it appears) and when I unplug my usb player these 3 doesn't appear again

---

### Post by andybleaden on 2008-03-12
Which type of mp3 are you trying to use?

---

### Post by ieshmutis on 2008-03-12
What do you mean which type? well it's s1mp3 the one which plays *.mp3 *.wav and *.amv files, usb 2.0.

I'm sorry for being noobish, my english is not good and I'm new to linux :)

---

### Post by Gen2ly on 2008-03-12
dmesg hmm, I use:

```
tail -f /var/logs/messages
```

and am able to see what device it is after I plug it in.  Perhaps this will give more info.

---

### Post by ieshmutis on 2008-03-13
here's the output of "tail -f /var/logs/messages"
```

[  771.697929] usb 1-3: new full speed USB device using ohci_hcd and address 3
[  771.910064] usb 1-3: configuration #1 chosen from 1 choice
[  772.081417] usbcore: registered new interface driver libusual
[  772.125081] Initializing USB Mass Storage driver...
[  772.125645] scsi2 : SCSI emulation for USB Mass Storage devices
[  772.126440] usbcore: registered new interface driver usb-storage
[  772.126671] USB Mass Storage support registered.
[  777.133617] scsi 2:0:0:0: CD-ROM            CLCDROM  USB DISK         1.10 PQ: 0 ANSI: 2
[  777.140598] scsi 2:0:0:1: Direct-Access     USB 2.0  (FS) FLASH DISK  1.00 PQ: 0 ANSI: 0 CCS
[  777.214041] usb 1-3: USB disconnect, address 3
[  777.214601] sr0: scsi3-mmc drive: 0x/0x caddy
[  779.125203] usb 1-3: new full speed USB device using ohci_hcd and address 4
[  779.337362] usb 1-3: configuration #1 chosen from 1 choice
[  779.340399] scsi3 : SCSI emulation for USB Mass Storage devices
[  784.344919] scsi 3:0:0:0: CD-ROM            CLCDROM  USB DISK         1.10 PQ: 0 ANSI: 2
[  784.351895] scsi 3:0:0:1: Direct-Access     USB 2.0  (FS) FLASH DISK  1.00 PQ: 0 ANSI: 0 CCS
[  784.381369] usb 1-3: USB disconnect, address 4
[  784.381897] sr0: scsi3-mmc drive: 0x/0x caddy [  784.382038] sr 3:0:0:0: Attached scsi generic sg0 type 5
[  784.384463] sd 3:0:0:1: [sda] READ CAPACITY failed
[  784.384471] sd 3:0:0:1: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  784.384475] sd 3:0:0:1: [sda] Sense not available.
[  784.388181] sd 3:0:0:1: [sda] Write Protect is off
[  784.388274] sd 3:0:0:1: [sda] Attached SCSI removable disk
[  784.388330] sd 3:0:0:1: Attached scsi generic sg1 type 0
[  786.352473] usb 1-3: new full speed USB device using ohci_hcd and address 5
[  786.564643] usb 1-3: configuration #1 chosen from 1 choice
[  786.567778] scsi4 : SCSI emulation for USB Mass Storage devices
[  791.572193] scsi 4:0:0:0: CD-ROM            CLCDROM  USB DISK         1.10 PQ: 0 ANSI: 2
[  791.579200] scsi 4:0:0:1: Direct-Access     USB 2.0  (FS) FLASH DISK  1.00 PQ: 0 ANSI: 0 CCS
[  791.608635] usb 1-3: USB disconnect, address 5
[  791.609180] sr0: scsi3-mmc drive: 0x/0x caddy
[  791.609323] sr 4:0:0:0: Attached scsi generic sg0 type 5
[  791.611774] sd 4:0:0:1: [sda] READ CAPACITY failed
[  791.611782] sd 4:0:0:1: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  791.611786] sd 4:0:0:1: [sda] Sense not available.
[  791.613767] sd 4:0:0:1: [sda] Write Protect is off
[  791.613866] sd 4:0:0:1: [sda] Attached SCSI removable disk
[  791.613926] sd 4:0:0:1: Attached scsi generic sg1 type 0
[  793.583836] usb 1-3: new full speed USB device using ohci_hcd and address 6
[  793.795907] usb 1-3: configuration #1 chosen from 1 choice
[  793.798938] scsi5 : SCSI emulation for USB Mass Storage devices
[  798.803453] scsi 5:0:0:0: CD-ROM            CLCDROM  USB DISK         1.10 PQ: 0 ANSI: 2

```

I don't understand anything except that it repeatedly connects and then for some reason disconnects.. to make sure I just tried it on windows again and well it's working good without disconnections.

---

### Post by andybleaden on 2008-03-13
Sorry what make is the mp3...ie is it a sony, ipod, creative or another name?

Some are hard and or different to work with under linux

---

### Post by ieshmutis on 2008-03-13
oh it's MSI Digi Player

---

