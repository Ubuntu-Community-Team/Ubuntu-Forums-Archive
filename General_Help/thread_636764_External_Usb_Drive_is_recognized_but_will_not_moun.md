---
title: "External Usb Drive is recognized but will not mount"
date: 2007-12-10
forum: General Help
---

### Post by sidrit on 2007-12-10
i'm having lately a very annoying problem with my external usb drive.

i'm running Gutsy on an amd64 Dell Dimension C521.
the external drive is a 100Gb Fujitsu, which for a very long time worked just fine.

now when i connect the device, it gets listed in lsusb:

sid@dev:~$ lsusb 
Bus 002 Device 008: ID 048d:8903 Integrated Technology Express, Inc. 
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 003: ID 0461:4d15 Primax Electronics, Ltd 
Bus 002 Device 002: ID 0424:2504 Standard Microsystems Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Being the one on Device 008.

Up until here all is good.



sid@dev:~$ dmesg
[ 1778.851567] usb 2-3: new high speed USB device using ehci_hcd and address 8
[ 1788.965491] usb 2-3: configuration #1 chosen from 1 choice
[ 1788.966097] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1788.966214] usb-storage: device found at 8
[ 1788.966216] usb-storage: waiting for device to settle before scanning
[ 1794.954509] usb-storage: device scan complete
[ 1800.556329] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[ 1810.789815] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[ 1811.049356] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[ 1813.928228] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0 CCS
[ 1813.930457] sd 6:0:0:0: [sdb] 117573378 512-byte hardware sectors (60198 MB)
[ 1813.934448] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1813.934451] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1813.936443] sd 6:0:0:0: [sdb] 117573378 512-byte hardware sectors (60198 MB)
[ 1813.940436] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1813.940438] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1813.940440]  sdb:<6>usb 2-3: reset high speed USB device using ehci_hcd and address 8


The reseting keeps going on and on and the drive never settles.

also :
sid@dev:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5eff4ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9375    75304656   83  Linux
/dev/sda2            9376        9726     2819407+   5  Extended
/dev/sda5            9376        9726     2819376   82  Linux swap / Solaris

I can't even try to mount it manually since it's nowhere.


sid@dev:~$ cat /proc/bus/usb/devices
T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=048d ProdID=8903 Rev= 2.00
S:  Manufacturer=ITE TECH. INC.
S:  Product=USB TO IDE
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms



It's a few days i'm reading around basically in all sorts of forums about all sorts of trick such as removin  ehci_hcd, which then gets replaced by  ohci_hcd.
even read about disabling this last one which takes out  my usb plugs so that's a no go.

basically i just need this device to run one more time , for me to back up  the data.
don't really care about the disk itself.

anybody got any ideas?


thanks in advance .



sid

---

### Post by sidrit on 2007-12-10
have done basically no substantial changes to anything but i just got this from dmesg:


Dec 10 14:49:43 dev kernel: [  953.335658] usb 2-8: new high speed USB device using ehci_hcd and address 6
Dec 10 14:49:53 dev kernel: [  963.453723] usb 2-8: configuration #1 chosen from 1 choice
Dec 10 14:49:53 dev kernel: [  963.454072] scsi5 : SCSI emulation for USB Mass Storage devices
Dec 10 14:50:05 dev kernel: [  975.044859] usb 2-8: reset high speed USB device using ehci_hcd and address 6
Dec 10 14:50:15 dev kernel: [  985.270581] usb 2-8: reset high speed USB device using ehci_hcd and address 6
Dec 10 14:50:15 dev kernel: [  985.518138] usb 2-8: reset high speed USB device using ehci_hcd and address 6
Dec 10 14:50:17 dev kernel: [  987.570765] scsi 5:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0 CCS
Dec 10 14:50:17 dev kernel: [  987.572994] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Dec 10 14:50:17 dev kernel: [  987.573278] sd 5:0:0:0: [sdb] READ CAPACITY(16) failed
Dec 10 14:50:17 dev kernel: [  987.573281] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 10 14:50:17 dev kernel: [  987.573284] sd 5:0:0:0: [sdb] Use 0xffffffff as device size
Dec 10 14:50:17 dev kernel: [  987.573288] sd 5:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Dec 10 14:50:17 dev kernel: [  987.576987] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec 10 14:50:17 dev kernel: [  987.578980] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Dec 10 14:50:17 dev kernel: [  987.579107] sd 5:0:0:0: [sdb] READ CAPACITY(16) failed
Dec 10 14:50:17 dev kernel: [  987.579109] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 10 14:50:17 dev kernel: [  987.579112] sd 5:0:0:0: [sdb] Use 0xffffffff as device size
Dec 10 14:50:17 dev kernel: [  987.579115] sd 5:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Dec 10 14:50:17 dev kernel: [  987.582974] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec 10 14:50:48 dev kernel: [  987.582979]  sdb:<6>usb 2-8: reset high speed USB device using ehci_hcd and address 6

---

