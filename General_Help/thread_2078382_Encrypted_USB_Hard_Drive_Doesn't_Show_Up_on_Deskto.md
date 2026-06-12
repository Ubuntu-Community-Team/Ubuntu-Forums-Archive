---
title: "Encrypted USB Hard Drive Doesn't Show Up on Desktop or in Nautilus in 12.10"
date: 2012-10-30
forum: General Help
---

### Post by linux4me on 2012-10-30
I have done a clean install of 12.10 AMD64 from a USB drive to a 500 GB hard drive. It is set up with the full-disk encryption and LVM options. The installation went smoothly with no errors, and the system boots up and seems to work just fine except for one problem.

My /home directory is backed up on a 1.0 TB USB hard drive that is also set up with encryption and LVM. When I plug it in to the new system, It appears to mount, but the icon doesn't show up on my desktop or in the launcher and it doesn't show up in Nautilus, /mnt, or /media. 

In 12.04, when I connect this drive it automounts and I am prompted for the passphrase; once I enter it, it appears in the launcher and in Nautilus, so this appears to be a problem just in 12.10.

The output of dmesg looks like this:
```
[   85.644059] usb 1-5: >new high-speed USB device number 3 using ehci_hcd
[   85.777102] usb 1-5: >New USB device found, idVendor=152d, idProduct=0539
[   85.777114] usb 1-5: >New USB device strings: Mfr=1, Product=11, SerialNumber=3
[   85.777122] usb 1-5: >Product: USB3.0 Device
[   85.777129] usb 1-5: >Manufacturer: JMicron
[   85.777137] usb 1-5: >SerialNumber: BBA00000016B
[   85.860892] Initializing USB Mass Storage driver...
[   85.862923] scsi6 : usb-storage 1-5:1.0
[   85.863381] usbcore: registered new interface driver usb-storage
[   85.863386] USB Mass Storage support registered.
[   85.876215] usbcore: registered new interface driver uas
[   86.861124] scsi 6:0:0:0: >Direct-Access     Generic  USB3.0                PQ: 0 ANSI: 2 CCS
[   86.864485] sd 6:0:0:0: >[sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   86.864778] sd 6:0:0:0: >Attached scsi generic sg2 type 0
[   86.865340] sd 6:0:0:0: >[sdb] Write Protect is off
[   86.865349] sd 6:0:0:0: >[sdb] Mode Sense: 28 00 00 00
[   86.866187] sd 6:0:0:0: >[sdb] No Caching mode page present
[   86.866196] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[   86.870438] sd 6:0:0:0: >[sdb] No Caching mode page present
[   86.870449] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[   87.160071]  sdb: sdb1
[   87.164646] sd 6:0:0:0: >[sdb] No Caching mode page present
[   87.164654] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[   87.164659] sd 6:0:0:0: >[sdb] Attached SCSI disk
```

And lsusb looks like this:
```
Bus 001 Device 003: ID 152d:0539 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 002 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The drive does appear when I run fdisk -l:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d833f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
/dev/sda5          501760   976771071   488134656   83  Linux

Disk /dev/mapper/sdb5_crypt: 499.8 GB, 499847790592 bytes
255 heads, 63 sectors/track, 60769 cylinders, total 976265216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu-root: 495.8 GB, 495770927104 bytes
255 heads, 63 sectors/track, 60274 cylinders, total 968302592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu-swap_1: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7fb55d1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   8e  Linux LVM
```

I installed gnome-system-tools and ran Users and Groups. My user does have the "Access external storage devices automatically" option checked.

I verified that automount is set to true in gsettings.

I attached another, unencrypted mass storage device, and it was automounted and displays normally, so I am leaning toward the encryption as being the culprit, but I'm not sure.

I still have a 12.04 machine that recognizes the drive, so I can use it to compare outputs. The user name on both machines--and the owner of the drive I set when I set up the USB drive--are the same.

Has anyone had a similar problem and found a solution?

---

### Post by linux4me on 2012-10-31
I haven't found a fix for this yet, but I do now have a workaround, and it appears that what is happening is that the encrypted drive is recognized, but there is no prompt for the passphrase and the drive is not automounted, so it's not showing up in the Launcher and Nautilus.

The workaround is as follows:
[LIST=1]
[*]Open Disks (Disk Utility in 12.04) by pressing the Super (Windows) key and typing in "Disks." Click the Disks icon.
[*]Locate the encrypted USB drive if it's already plugged in, or plug it in if it's not and it will appear in the left column under Disk Drives.
[*]Click the ecrypted drive in Disk Drives to select it.
[*]In the Volumes section, click the padlock icon and enter the passphrase in the dialog that pops up to unlock the drive.
[*]Click the filesystem that appears in Volumes once the drive is unlocked.
[*]Click the icon to mount the file system.
[/LIST]

The drive should now appear in the Launcher and in Nautilus in the Computer section (not in Devices as in 12.04) and you can use it as usual.

If anyone knows what package is at fault for the failure to automount the drive, I would be glad to file a bug on Launchpad, but I'm not sure which package it would be.

---

