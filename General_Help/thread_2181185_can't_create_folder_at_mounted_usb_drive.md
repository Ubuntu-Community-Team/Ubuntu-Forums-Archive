---
title: "can't create folder at mounted usb drive"
date: 2013-10-16
forum: General Help
---

### Post by Marchello_Lippi on 2013-10-16
Hi all, 

I can't create folder at mounted usb drive, please see details below and help me if possible. 


$ sudo mount -o rw -t ntfs /dev/sda1 /mnt/wd
$ mkdir /mnt/wd/tmp1
mkdir: Can't create folder `/mnt/wd/tmp1': Permission denied
$ sudo mkdir /mnt/wd/tmp1
mkdir: Can't create folder `/mnt/wd/tmp1': Operation not permitted

$ dmesg 
[331676.587446] usbcore: registered new interface driver usblp
[701964.930721] usb 1-1.3: new high-speed USB device number 4 using dwc_otg
[701965.032593] usb 1-1.3: New USB device found, idVendor=05e3, idProduct=0610
[701965.032624] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[701965.032641] usb 1-1.3: Product: USB2.0 Hub
[701965.035487] hub 1-1.3:1.0: USB hub found
[701965.036363] hub 1-1.3:1.0: 4 ports detected
[701965.310939] usb 1-1.3.1: new high-speed USB device number 5 using dwc_otg
[701965.412516] usb 1-1.3.1: New USB device found, idVendor=05e3, idProduct=0610
[701965.412548] usb 1-1.3.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[701965.412564] usb 1-1.3.1: Product: USB2.0 Hub
[701965.413710] hub 1-1.3.1:1.0: USB hub found
[701965.414288] hub 1-1.3.1:1.0: 4 ports detected
[703125.302845] usb 1-1.3: USB disconnect, device number 4
[703125.302877] usb 1-1.3.1: USB disconnect, device number 5
[703128.101739] usb 1-1.2: new high-speed USB device number 6 using dwc_otg
[703128.203492] usb 1-1.2: New USB device found, idVendor=05e3, idProduct=0610
[703128.203523] usb 1-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[703128.203540] usb 1-1.2: Product: USB2.0 Hub
[703128.207094] hub 1-1.2:1.0: USB hub found
[703128.207649] hub 1-1.2:1.0: 4 ports detected
[703128.481850] usb 1-1.2.1: new high-speed USB device number 7 using dwc_otg
[703128.583542] usb 1-1.2.1: New USB device found, idVendor=05e3, idProduct=0610
[703128.583573] usb 1-1.2.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[703128.583589] usb 1-1.2.1: Product: USB2.0 Hub
[703128.584828] hub 1-1.2.1:1.0: USB hub found
[703128.586377] hub 1-1.2.1:1.0: 4 ports detected
[703299.949388] usb 1-1.2.1.2: new high-speed USB device number 8 using dwc_otg
[703300.050857] usb 1-1.2.1.2: New USB device found, idVendor=1058, idProduct=1010
[703300.050886] usb 1-1.2.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[703300.050903] usb 1-1.2.1.2: Product: External HDD    
[703300.050918] usb 1-1.2.1.2: Manufacturer: Western Digital 
[703300.050932] usb 1-1.2.1.2: SerialNumber: 57442D575837314142304335383230
[703300.057353] scsi0 : usb-storage 1-1.2.1.2:1.0
[703301.050379] scsi 0:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[703301.053928] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[703301.054624] sd 0:0:0:0: [sda] Write Protect is off
[703301.054655] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[703301.055253] sd 0:0:0:0: [sda] No Caching mode page present
[703301.055280] sd 0:0:0:0: [sda] Assuming drive cache: write through
[703301.058003] sd 0:0:0:0: [sda] No Caching mode page present
[703301.058034] sd 0:0:0:0: [sda] Assuming drive cache: write through
[703301.063859]  sda: sda1
[703301.068790] sd 0:0:0:0: [sda] No Caching mode page present
[703301.068823] sd 0:0:0:0: [sda] Assuming drive cache: write through
[703301.068843] sd 0:0:0:0: [sda] Attached SCSI disk
[703325.716399] NTFS driver 2.1.30 [Flags: R/W MODULE].
[703325.867134] NTFS volume version 3.1.
[703967.556936] EXT4-fs (sda): VFS: Can't find ext4 filesystem
[703967.560435] EXT4-fs (sda): VFS: Can't find ext4 filesystem
[703967.570313] EXT4-fs (sda): VFS: Can't find ext4 filesystem
[703967.580448] FAT-fs (sda): invalid media value (0xb9)
[703967.580473] FAT-fs (sda): Can't find a valid FAT filesystem
[703967.590575] FAT-fs (sda): invalid media value (0xb9)
[703967.590599] FAT-fs (sda): Can't find a valid FAT filesystem
[703967.600446] NTFS-fs warning (device sda): is_boot_sector_ntfs(): Invalid boot sector checksum.
[703967.600481] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[703967.600498] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[703967.600513] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[704008.362992] FAT-fs (sda): invalid media value (0xb9)
[704008.363017] FAT-fs (sda): Can't find a valid FAT filesystem
[704033.595902] FAT-fs (sda1): bogus number of reserved sectors
[704033.595930] FAT-fs (sda1): Can't find a valid FAT filesystem
[704041.497866] NTFS volume version 3.1.
[704660.357921] NTFS volume version 3.1.
[704694.581639] NTFS volume version 3.1.
[705075.564712] NTFS volume version 3.1.
[705225.104677] NTFS volume version 3.1.
[705319.942056] NTFS volume version 3.1.

---

### Post by cariboo on 2013-10-16
It looks like you may have to run scandisk on the the drive before you can do anything with it.

---

