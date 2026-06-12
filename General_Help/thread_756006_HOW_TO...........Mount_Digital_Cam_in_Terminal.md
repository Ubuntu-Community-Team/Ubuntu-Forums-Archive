---
title: "HOW TO...........Mount Digital Cam in Terminal"
date: 2008-04-15
forum: General Help
---

### Post by jeffsa12 on 2008-04-15
I have an old Samsung Digimax 130 camera. It connects through USB. Windows reads it as a mass storage device as soom as it's plugged in without the need for drivers, etc.

How do I get Nautilus to show it as if its a thumb drive? I'm running Ubuntu 7.10 with a Vbox WinXP and after screwing around a bit, I was able to get Win Explorer to read via USB.....but not Ubuntu!!!

It seems its something simple if virtual WinXP will read it through Ubuntu.
How to mount...unmount.... In a terminal?

Can I install code in fstab to auto mount, showing in Nautilus, then unmount using GUI?

What code would I insert?



jeff@jeff-new-dsktp:~$ tail -f /var/log/messages
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.591913] sd 8:0:0:0: [sde] READ CAPACITY failed
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.591920] sd 8:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.591926] sd 8:0:0:0: [sde] Sense not available.
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592798] sd 8:0:0:0: [sde] Write Protect is off
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592909] sd 8:0:0:0: [sde] READ CAPACITY failed
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592914] sd 8:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592920] sd 8:0:0:0: [sde] Sense not available.
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.592936] sd 8:0:0:0: [sde] Write Protect is off
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.593011] sd 8:0:0:0: [sde] Attached SCSI removable disk
Apr 14 14:10:33 jeff-new-dsktp kernel: [ 9637.593082] sd 8:0:0:0: Attached scsi generic sg4 type 0
Apr 14 14:11:02 jeff-new-dsktp kernel: [ 9666.279157] usb 1-2: new full speed USB device using ohci_hcd and address 6
Apr 14 14:11:02 jeff-new-dsktp kernel: [ 9666.488136] usb 1-2: configuration #1 chosen from 1 choice
Apr 14 14:11:02 jeff-new-dsktp kernel: [ 9666.490163] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 14 14:11:07 jeff-new-dsktp kernel: [ 9671.492327] scsi 9:0:0:0: Direct-Access SAMSUNG DIGIMAX 130 1.33 PQ: 0 ANSI: 0 CCS
Apr 14 14:11:07 jeff-new-dsktp kernel: [ 9671.502291] sd 9:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
Apr 14 14:11:37 jeff-new-dsktp kernel: [ 9701.647690] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:12:07 jeff-new-dsktp kernel: [ 9731.997272] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:12:38 jeff-new-dsktp kernel: [ 9762.334863] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:13:08 jeff-new-dsktp kernel: [ 9792.688427] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:13:39 jeff-new-dsktp kernel: [ 9823.038017] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:14:09 jeff-new-dsktp kernel: [ 9853.387576] usb 1-2: reset full speed USB device using ohci_hcd and address 6
Apr 14 14:14:09 jeff-new-dsktp kernel: [ 9853.593818] sd 9:0:0:0: [sde] Write Protect is off
Apr 14 14:14:09 jeff-new-dsktp kernel: [ 9853.611736] sd 9:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)




dmesg showed:

[ 9896.952842] end_request: I/O error, dev sde, sector 0
[ 9896.953215] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9896.953223] end_request: I/O error, dev sde, sector 0
[ 9896.953232] unable to read partition table
[ 9896.953726] sd 9:0:0:0: [sde] Attached SCSI removable disk
[ 9896.953800] sd 9:0:0:0: Attached scsi generic sg4 type 0
[ 9978.018634] usb 1-2: new full speed USB device using ohci_hcd and address 7
[ 9978.227618] usb 1-2: configuration #1 chosen from 1 choice
[ 9978.229649] scsi10 : SCSI emulation for USB Mass Storage devices
[ 9978.229903] usb-storage: device found at 7
[ 9978.229907] usb-storage: waiting for device to settle before scanning
[ 9983.225811] usb-storage: device scan complete
[ 9983.231806] scsi 10:0:0:0: Direct-Access SAMSUNG DIGIMAX 130 1.33 PQ: 0 ANSI: 0 CCS
[ 9983.241770] sd 10:0:0:0: [sde] 15600 512-byte hardware sectors (8 MB)
[10013.387180] usb 1-2: reset full speed USB device using ohci_hcd and address 7
[10043.744743] usb 1-2: reset full speed USB device using ohci_hcd and address 7

---

### Post by strabes on 2008-04-15
Please paste the output of this command:```
sudo fdisk -l
```

If you don't have any other drives plugged in, the camera card should be located at /dev/sdb1. So you could mount it with something like this:
```
sudo mkdir /media/cameracard
sudo mount /dev/sdb1 /media/cameracard
```

---

### Post by jeffsa12 on 2008-04-18
Hey strabes......thanks for the help.

Below are the results for sudo fdisk -l

I tried the code you suggest, and with several slight variations to mount my camera....nothing worked. I used the tab key to get all 725 possibilities for sudo mount /dev/ . Tried several but no luck.....

jeff@jeff-new-dsktp:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         393        6989    52990400    7  HPFS/NTFS
/dev/hda2               1         392     3148708+   b  W95 FAT32
/dev/hda3            6996       19457   100101015    f  W95 Ext'd (LBA)
/dev/hda5            6996        8955    15743668+   b  W95 FAT32
/dev/hda6            8956        9214     2080386   82  Linux swap / Solaris
/dev/hda7            9215       10141     7446096   83  Linux
/dev/hda8           10142       11068     7446096   83  Linux
/dev/hda9           11069       11995     7446096   83  Linux
/dev/hda10          11996       12922     7446096   83  Linux
/dev/hda11          12923       19457    52492356    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71d4ff44

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2   *           1        1313    10546641    7  HPFS/NTFS
/dev/hdb3            1314        9723    67553325    f  W95 Ext'd (LBA)
/dev/hdb5            1314        2376     8538516    b  W95 FAT32
/dev/hdb6            2377        2638     2104483+  82  Linux swap / Solaris
/dev/hdb7            2639        3565     7446096   83  Linux
/dev/hdb8            3566        9723    49464103+  83  Linux
jeff@jeff-new-dsktp:~$

---

