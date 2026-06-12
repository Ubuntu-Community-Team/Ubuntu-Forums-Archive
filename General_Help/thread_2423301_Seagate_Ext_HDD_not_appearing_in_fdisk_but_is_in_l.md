---
title: "Seagate Ext HDD not appearing in fdisk but is in lsusb"
date: 2019-07-20
forum: General Help
---

### Post by awbaader on 2019-07-20
Hi, I have an old(ish) 3tb Seagate HDD that has a lot of material on it and I wish to transfer it to my snazzy new external HDD. I'm having no end of problems doing so.
When I first booted my laptop with the HDD plugged in it appeared in Dolphin but wouldn't mount it. It gave the error:
> An error occurred while accessing 'Seagate Expansion Drive', the system responded: An unspecified error has occurred: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken

So I used testdisk to rewrite the file system and I could access it via Dolphin. I started copying data across and after about 20 minutes it crapped out and now it doesn't appear in Dolphin at all. It is still appearing in lsusb
```
andy@rsehole:~$ lsusb
Bus 002 Device 003: ID 04f2:b52d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 248a:8366  
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bc2:3320 Seagate RSS LLC SRD00F2 [Expansion Desktop Drive]
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

It also doesn't appear with sudo fdisk -l

When I connect it dmesg gives:
```
[  791.085934] usb 3-2: New USB device found, idVendor=248a, idProduct=8366, bcdDevice= 1.00
[  791.085943] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  791.085947] usb 3-2: Product: 2.4G Mouse
[  791.085951] usb 3-2: Manufacturer: Telink
[  791.116913] input: Telink 2.4G Mouse Mouse as /devices/pci0000:00/0000:00:10.0/usb3/3-2/3-2:1.0/0003:248A:8366.0002/input/input16
[  791.176601] input: Telink 2.4G Mouse Consumer Control as /devices/pci0000:00/0000:00:10.0/usb3/3-2/3-2:1.0/0003:248A:8366.0002/input/input17
[  791.176886] input: Telink 2.4G Mouse System Control as /devices/pci0000:00/0000:00:10.0/usb3/3-2/3-2:1.0/0003:248A:8366.0002/input/input18
[  791.177168] hid-generic 0003:248A:8366.0002: input,hidraw0: USB HID v1.11 Mouse [Telink 2.4G Mouse] on usb-0000:00:10.0-2/input0
[  798.403575] usb 1-1.1: new high-speed USB device number 5 using ehci-pci
[  798.558461] usb 1-1.1: New USB device found, idVendor=0bc2, idProduct=3320, bcdDevice= 1.00
[  798.558499] usb 1-1.1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[  798.558504] usb 1-1.1: Product: Expansion Desk
[  798.558508] usb 1-1.1: Manufacturer: Seagate
[  798.558511] usb 1-1.1: SerialNumber: 2HC015KJ
[  798.560804] scsi host3: uas
[  798.562471] scsi 3:0:0:0: Direct-Access     Seagate  Expansion Desk   0711 PQ: 0 ANSI: 6
[  798.564513] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  798.565203] sd 3:0:0:0: [sdc] Spinning up disk...
[  799.575484] ...........ready
[  809.816599] sd 3:0:0:0: [sdc] 732566645 4096-byte logical blocks: (3.00 TB/2.73 TiB)
```

So it is seeing the thing but I have no idea what to do next. I had a look with gparted but it isn't showing up there either.

I'm at a complete loss. I really don't want to lose this data. Yeah, I know that no one wants to lose data but it's something like 10 year's worth of photos and the like.
Any help will be greatly, greatly appreciated.

Andy

UPDATE

I rebooted with the device plugged in and ran dmesg again. It now gives:
```
[  168.898401] xhci_hcd 0000:00:10.0: bad transfer trb length 16777210 in event trb
[  168.914306] scsi host3: uas_eh_device_reset_handler start
[  175.026271] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  180.402145] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  180.610068] usb 4-1: device not accepting address 6, error -62
[  186.034167] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  191.414216] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  191.621999] usb 4-1: device not accepting address 6, error -62
[  197.042023] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  202.418072] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  202.625980] usb 4-1: device not accepting address 6, error -62
[  208.050046] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  213.426088] xhci_hcd 0000:00:10.0: Timeout while waiting for setup device command
[  213.633866] usb 4-1: device not accepting address 6, error -62
[  213.690143] usb 4-1: USB disconnect, device number 6


```
Device 6 being my external HDD

---

### Post by TheFu on 2019-07-20
Try a different USB cable and different port.  If those don't help, might be the USB controller inside the drive. Can you "shuck" the drive and put it into a different enclosure or use a dock?

---

### Post by awbaader on 2019-07-21
I tried that this morning and weirdly the drive stopped showing up in lsusb and there was just a blank entry. The drive was still spinning up though and making noises as though something was happening in there.
I tried using gnome-disks but again it wasn't showing up.
I've never had to shuck a drive before. Tbh I had to Google to see what that was. Perhaps I should try that next weekend. 
Thanks. :)

---

### Post by zio-pietro on 2019-11-16
Hi,
the same problem here: HD Seagate Barracuda 7200.10 250 GB attached thru SATA->USB adapter. And now I can se this strange thing:
from /var/log/syslog : > ... kernel: [478980.453892] sd 6:0:0:0: [sdb] Attached SCSI disk
from ls -l /dev/sd*: 
> brw-rw---- 1 root disk 8,  0 Nov 10 23:16 /dev/sda
brw-rw---- 1 root disk 8,  1 Nov 10 23:17 /dev/sda1
brw-rw---- 1 root disk 8, 16 Nov 16 12:15 /dev/sdb
from fdisk -l : > /dev/sda1  *     2048 976771071 976769024 465.8G 83 Linux  (only sda)
and obviously fdisk /dev/sdb > /dev/sdb: fdisk: cannot open /dev/sdb: No such file or directory

Still didn't discovered the reason of this behavior. Any hint is highly appreciaated. Tnx.

---

### Post by oldfred on 2019-11-16
@zio-pietro
What format was external drive?
If NTFS and you mounted it with Windows, it may still have fast startup/hibernation flags set. Then Linux will not mount it to prevent damage to hibernation.
You may be able to manually force mount in read only mode, but gui tools default to read/write and will not mount.

Some with external drives do not partition drive. Almost all tools expect partitions, but some can write data to drive as if it was an old floppy drive that did not have partitions. So if no sdb1, that is a possibility. You may be able to force mount like a floppy drive, but floppy drive, drivers are being discontinued.

---

