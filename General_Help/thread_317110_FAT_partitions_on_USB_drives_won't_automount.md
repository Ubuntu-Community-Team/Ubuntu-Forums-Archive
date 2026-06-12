---
title: "FAT partitions on USB drives won't automount"
date: 2006-12-11
forum: General Help
---

### Post by cracker on 2006-12-11
I have Ubuntu 6.10 happily installed on my desktop system. However, it refuses to automount FAT partitions on USB sticks. However, it mounts ext3 partitions just fine (on the same USB stick I installed from, which has both a FAT and ext3 partition on it). Any idea why?

---

### Post by x64Jimbo on 2006-12-11
What errors are you getting?

---

### Post by cracker on 2006-12-11
I wasn't getting any at all. I just now attached it again to check if anything showed up in dmesg, and it mounted the FAT partition, for the first time. Odd, I'll be sure to post here again if it stops working.

---

### Post by anasofiapaixao on 2006-12-28
I am getting the same problem. My mp3 player turns on, charges, but just won't communicate with the computer. This happens with another 128MB player also. Any ideias? :?

---

### Post by x64Jimbo on 2006-12-28
What kind of mp3 player? Are you sure it's a FAT32 partition? Have you tried mounting it with the mount command?

---

### Post by splot on 2007-01-04
I don't know about the mp3 player, but my palm SD card (in a thumbdrive card reader) won't automount, and I can't find the device to mount it from the command line.  Maybe it's fat?  that'd make sense I guess...

---

### Post by cracker on 2007-01-08
I had the same problem on my brother's computer. On a fresh install of Edgy, USB devices that use FAT filesystems won't automount. I could easily mount it by doing the following:'

```
$ sudo mkdir /media/usb
$ sudo chmod 777 /media/usb
$ sudo mount /dev/sdc1 /media/usb
```
I'll be playing with it, and paying more attention this time. If I fix it, I'll reply how.

---

### Post by dcstar on 2007-01-08
Check that the **gnome-volume-automount**(? spelling) process is running.

---

### Post by cracker on 2007-01-11
Gnome-volume-automount isn't running, and can't be found using slocate. Here is a dmesg:

```
[17182243.152000] usb 3-1: new high speed USB device using ehci_hcd and address 2
[17182243.300000] usb 3-1: configuration #1 chosen from 1 choice
[17182243.300000] hub 3-1:1.0: USB hub found
[17182243.300000] hub 3-1:1.0: 1 port detected
[17182243.604000] usb 3-1.1: new high speed USB device using ehci_hcd and address 3
[17182243.712000] usb 3-1.1: configuration #1 chosen from 1 choice
[17182243.868000] usbcore: registered new driver libusual
[17182243.944000] Initializing USB Mass Storage driver...
[17182243.944000] scsi0 : SCSI emulation for USB Mass Storage devices
[17182243.944000] usb-storage: device found at 3
[17182243.944000] usb-storage: waiting for device to settle before scanning
[17182243.944000] usbcore: registered new driver usb-storage
[17182243.944000] USB Mass Storage support registered.
[17182248.944000] usb-storage: device scan complete
[17182248.944000]   Vendor: Corsair   Model: Flash Voyager     Rev: 1.00
[17182248.944000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182249.004000] SCSI device sda: 8011776 512-byte hdwr sectors (4102 MB)
[17182249.008000] sda: Write Protect is off
[17182249.008000] sda: Mode Sense: 00 26 00 00
[17182249.008000] sda: assuming drive cache: write through
[17182249.012000] SCSI device sda: 8011776 512-byte hdwr sectors (4102 MB)
[17182249.016000] sda: Write Protect is off
[17182249.016000] sda: Mode Sense: 00 26 00 00
[17182249.016000] sda: assuming drive cache: write through
[17182249.016000]  sda: sda1
[17182249.020000] sd 0:0:0:0: Attached scsi removable disk sda
[17182249.032000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[COLOR="DarkRed"][17182250.072000] UDF-fs: No VRS found
[17182250.192000] Unable to identify CD-ROM format.[/COLOR]

```

---

### Post by cracker on 2007-01-11
Gnome-volume-automount isn't running on the working systems either..."gnome-volume-ma"nager is running on both systems. Here is dmesg from a working system:

```
[17688300.280000] usb 2-9: new high speed USB device using ehci_hcd and address 6
[17688300.424000] usb 2-9: configuration #1 chosen from 1 choice
[17688300.424000] hub 2-9:1.0: USB hub found
[17688300.428000] hub 2-9:1.0: 1 port detected
[17688300.732000] usb 2-9.1: new high speed USB device using ehci_hcd and address 7
[17688300.836000] usb 2-9.1: configuration #1 chosen from 1 choice
[17688300.840000] scsi5 : SCSI emulation for USB Mass Storage devices
[17688300.840000] usb-storage: device found at 7
[17688300.840000] usb-storage: waiting for device to settle before scanning
[17688305.840000] usb-storage: device scan complete
[17688305.840000]   Vendor: Corsair   Model: Flash Voyager     Rev: 1.00
[17688305.840000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17688305.840000] SCSI device sdd: 8011776 512-byte hdwr sectors (4102 MB)
[17688305.844000] sdd: Write Protect is off
[17688305.844000] sdd: Mode Sense: 00 26 00 00
[17688305.844000] sdd: assuming drive cache: write through
[17688305.848000] SCSI device sdd: 8011776 512-byte hdwr sectors (4102 MB)
[17688305.852000] sdd: Write Protect is off
[17688305.852000] sdd: Mode Sense: 00 26 00 00
[17688305.852000] sdd: assuming drive cache: write through
[17688305.852000]  sdd: sdd1
[17688305.856000] sd 5:0:0:0: Attached scsi removable disk sdd
[17688305.856000] sd 5:0:0:0: Attached scsi generic sg3 type 0
[COLOR="DarkRed"][17688306.264000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```[/COLOR]

I marked in red in both posts what I suspect is the difference that matters.

---

### Post by dcstar on 2007-01-12
> **cracker said:**
> Gnome-volume-automount isn't running on the working systems either..."gnome-volume-ma"nager is running on both systems. Here is dmesg from a working system:

```

.......
[17688305.856000] sd 5:0:0:0: Attached scsi removable disk sdd
[17688305.856000] sd 5:0:0:0: Attached scsi generic sg3 type 0
[COLOR="DarkRed"][17688306.264000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```[/COLOR]

I marked in red in both posts what I suspect is the difference that matters.

Yeah, that was my error, it should be the gnome-volume-manager.

For some reason one system is seeing the drive as a UDF and not FAT32, are there any differences between the systems such as custom kernels etc?

---

### Post by cracker on 2007-01-12
No, both systems were installed from the same source (Edgy i386 Desktop liveUSB), and while I have installed more packages on the one, I didn't do anything specifically aimed at USB storage devices. I have another machine that I installed using the alternate CD, and it does not have this problem.

---

### Post by cracker on 2007-01-12
Aha! You reminded me of one change I did. Because I installed using a USB stick, it created a cdrom entry in my fstab on the next available sdN. I removed it on the working machine when I had to edit the fstab to fix another problem, without thinking twice. Chock this one up as a glitch when installing from USB.

---

