---
title: "LUKS partition won't mount"
date: 2014-08-12
forum: General Help
---

### Post by jonnsl on 2014-08-12
Hi,

I created an encrypted partition in a external HD using the disk utility, it worked just fine for a while, but now the partition won't mount. Ubuntu asks for the password then nothing happens.

dmesg says this:
```
[17174.785358] usb 2-1.4: new high-speed USB device number 7 using ehci-pci[17174.878921] usb 2-1.4: New USB device found, idVendor=1058, idProduct=1110
[17174.878928] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[17174.878932] usb 2-1.4: Product: My Book 1110
[17174.878936] usb 2-1.4: Manufacturer: Western Digital
[17174.878939] usb 2-1.4: SerialNumber: [REDACTED]
[17174.998167] usb-storage 2-1.4:1.0: USB Mass Storage device detected
[17174.998237] scsi6 : usb-storage 2-1.4:1.0
[17174.998288] usbcore: registered new interface driver usb-storage
[17175.997978] scsi 6:0:0:0: Direct-Access     WD       My Book 1110     1030 PQ: 0 ANSI: 4
[17175.998850] scsi 6:0:0:1: CD-ROM            WD       Virtual CD 1110  1030 PQ: 0 ANSI: 4
[17175.999736] scsi 6:0:0:2: Enclosure         WD       SES Device       1030 PQ: 0 ANSI: 4
[17175.999978] sd 6:0:0:0: Attached scsi generic sg3 type 0
[17176.001311] sd 6:0:0:0: [sdc] 975400960 512-byte logical blocks: (499 GB/465 GiB)
[17176.004410] sd 6:0:0:0: [sdc] Write Protect is off
[17176.004414] sd 6:0:0:0: [sdc] Mode Sense: 23 00 10 00
[17176.006157] sr1: scsi3-mmc drive: 51x/51x caddy
[17176.006252] sr 6:0:0:1: Attached scsi CD-ROM sr1
[17176.006307] sr 6:0:0:1: Attached scsi generic sg4 type 5
[17176.006403] scsi 6:0:0:2: Attached scsi generic sg5 type 13
[17176.008117] sd 6:0:0:0: [sdc] No Caching mode page found
[17176.008121] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[17176.014048] sd 6:0:0:0: [sdc] No Caching mode page found
[17176.014053] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[17176.036494] ses 6:0:0:2: Attached Enclosure device
[17179.615382]  sdc: sdc1
[17179.623324] sd 6:0:0:0: [sdc] No Caching mode page found
[17179.623330] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[17179.623336] sd 6:0:0:0: [sdc] Attached SCSI disk
[17180.553260] UDF-fs: INFO Mounting volume 'WD SmartWare', timestamp 2009/10/14 18:49 (1f4c)
[17211.304268] sd 6:0:0:0: [sdc] Unhandled sense code
[17211.304275] sd 6:0:0:0: [sdc]  
[17211.304279] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[17211.304282] sd 6:0:0:0: [sdc]  
[17211.304284] Sense Key : Medium Error [current] 
[17211.304289] sd 6:0:0:0: [sdc]  
[17211.304292] Add. Sense: Unrecovered read error
[17211.304296] sd 6:0:0:0: [sdc] CDB: 
[17211.304298] Read(10): 28 00 00 00 10 3f 00 00 08 00
[17211.304309] end_request: critical medium error, dev sdc, sector 4159
[17211.304318] Buffer I/O error on device dm-1, logical block 0
[17211.304324] Buffer I/O error on device dm-1, logical block 1
```
the last 12 lines keeps repeating...

This is what fdisk -l says:
```
Disk /dev/sdd: 499.4 GB, 499405291520 bytes255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099d05


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   975386474   487693206   83  Linux
```

looks like there is a bad sector at 4159. Is this far enough to not have damaged the luks header? is it possible recover something? or is my data lost forever?

I really appreciate any help you can provide.

---

