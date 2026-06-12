---
title: "USB SD card reader reading wrong block count 14.04-&gt;16.04"
date: 2016-06-02
forum: General Help
---

### Post by kc7noa2 on 2016-06-02
Ok , ill start off with stating that the reader and SDcard was reading fine before update .... on Ubuntu 14.04 (intell i3 laptop)

SDcard has an OS for a SBC (odroid-x2) with ubuntu 14.04 ....

With Ubuntu 16.04 :

So in my laptop's internal SD card reader the block count is 
   [33178.492917] sd 13:0:0:0: [sdb] 125433856 512-byte logical blocks: (64.2 GB/59.8 GiB)

Using a USB card reader its shown as

   
33273.875949] sd 14:0:0:0: [sdb] 128 512-byte logical blocks: (65.5 kB/64.0 KiB)

Im thinking that the driver for the USB card reader is mis counting -- or more accurate has a 1,000,000 placement error -- 

here is dmesg with card into USB port with SDcard and internal reader ..

                        
33176.571242] usb 1-1.2: new high-speed USB device number 9 using ehci-pci
 [33176.678650] usb 1-1.2: New USB device found, idVendor=0bda, idProduct=0159
 [33176.678659] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
 [33176.678665] usb 1-1.2: Product: USB2.0-CRW
 [33176.678670] usb 1-1.2: Manufacturer: Generic
 [33176.678674] usb 1-1.2: SerialNumber: 20071114173400000
 [33176.684053] ums-realtek 1-1.2:1.0: USB Mass Storage device detected
 [33176.694697] scsi host13: usb-storage 1-1.2:1.0
 [33177.693968] scsi 13:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
 [33177.694830] sd 13:0:0:0: Attached scsi generic sg1 type 0
 [33178.492917] sd 13:0:0:0: [sdb] 125433856 512-byte logical blocks: (64.2 GB/59.8 GiB)
 [33178.494140] sd 13:0:0:0: [sdb] Write Protect is off
 [33178.494148] sd 13:0:0:0: [sdb] Mode Sense: 03 00 00 00
 [33178.495211] sd 13:0:0:0: [sdb] No Caching mode page found
 [33178.495220] sd 13:0:0:0: [sdb] Assuming drive cache: write through
 [33178.500335]  sdb: sdb1 sdb2
 [33178.503926] sd 13:0:0:0: [sdb] Attached SCSI removable disk
 [33178.945940] EXT4-fs (sdb2): recovery complete
 [33178.945948] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
 [33178.972239] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
 mike@mike-NV59C:~$  
 
 
 bad on USB reader
 
 
 33271.690552] usb 2-1.2: new high-speed USB device number 8 using ehci-pci
 [33271.971988] usb 2-1.2: New USB device found, idVendor=1307, idProduct=0310
 [33271.971995] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
 [33271.971999] usb 2-1.2: Product: Mass Storage Device
 [33271.972002] usb 2-1.2: Manufacturer: Generic
 [33271.972005] usb 2-1.2: SerialNumber: 00000000000006
 [33271.972419] usb-storage 2-1.2:1.0: USB Mass Storage device detected
 [33271.973283] scsi host14: usb-storage 2-1.2:1.0
 [33273.874270] scsi 14:0:0:0: Direct-Access     Generic  USB  SD Reader   0.00 PQ: 0 ANSI: 2
 [33273.875347] sd 14:0:0:0: Attached scsi generic sg1 type 0
 [33273.875949] sd 14:0:0:0: [sdb] 128 512-byte logical blocks: (65.5 kB/64.0 KiB)
 [33273.876693] sd 14:0:0:0: [sdb] Write Protect is off
 [33273.876699] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
 [33273.877275] sd 14:0:0:0: [sdb] No Caching mode page found
 [33273.877279] sd 14:0:0:0: [sdb] Assuming drive cache: write through
 [33273.881548]  sdb: sdb1 sdb2
 [33273.881556] sdb: p1 start 3072 is beyond EOD, enabling native capacity
 [33273.887057]  sdb: sdb1 sdb2
 [33273.887064] sdb: p1 start 3072 is beyond EOD, truncated
 [33273.887066] sdb: p2 start 266240 is beyond EOD, truncated
 [33273.889540] sd 14:0:0:0: [sdb] Attached SCSI removable disk
 mike@mike-NV59C:~$  
  
SD card is not corrupt -- the Odroid-X2 still boots and runs Ubuntu from the sdcard contents ...

mike@mike-NV59C:~$ uname -a
Linux mike-NV59C 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:15 UTC 2016 i686 i686 i686 GNU/Linux
mike@mike-NV59C:~$

---

