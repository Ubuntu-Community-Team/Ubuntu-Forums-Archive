---
title: "[SOLVED] problems mounting external harddisk"
date: 2007-10-28
forum: General Help
---

### Post by uroskriznar on 2007-10-28
I have problems mounting my external harddisk. Once I forgot to dismount it and just turned of my PC. Now Ubuntu doesn't find my external harddisk automaticaly and I don't know where to find it. Any ideas?

---

### Post by samosamo on 2007-10-28
unplug it and re-plug it back in.  post the last few relevant entries of "dmesg".

---

### Post by uroskriznar on 2007-10-29
I hope this is what you asked for.

[  286.242220] scsi 0:0:0:0: Direct-Access     Maxtor C ALYPSO           YAR4 PQ
: 0 ANSI: 0
[  286.283031] sd 0:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16                                                                            ).
[  286.283329] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
[  286.283332] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK                                                                            ,SUGGEST_OK
[  286.283336] sd 0:0:0:0: [sda] Use 0xffffffff as device size
[  286.283340] sd 0:0:0:0: [sda] 4294967296 512-byte hardware sectors (2199023 M                                                                            B)
[  286.284538] sd 0:0:0:0: [sda] Write Protect is off
[  286.284541] sd 0:0:0:0: [sda] Mode Sense: 00 08 00 00
[  286.284544] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  286.286144] sd 0:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16                                                                            ).
[  286.286332] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
[  286.286335] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK                                                                            ,SUGGEST_OK
[  286.286338] sd 0:0:0:0: [sda] Use 0xffffffff as device size
[  286.286342] sd 0:0:0:0: [sda] 4294967296 512-byte hardware sectors (2199023 M                                                                            B)
[  286.287519] sd 0:0:0:0: [sda] Write Protect is off
[  286.287522] sd 0:0:0:0: [sda] Mode Sense: 00 08 00 00
[  286.287524] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  286.287528]  sda:

---

### Post by uroskriznar on 2007-10-29
All of this is probably relevant as well:

[  286.242220] scsi 0:0:0:0: Direct-Access     Maxtor C ALYPSO           YAR4 PQ
: 0 ANSI: 0
[  286.283031] sd 0:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16
).
[  286.283329] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
[  286.283332] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
,SUGGEST_OK
[  286.283336] sd 0:0:0:0: [sda] Use 0xffffffff as device size
[  286.283340] sd 0:0:0:0: [sda] 4294967296 512-byte hardware sectors (2199023 M
B)
[  286.284538] sd 0:0:0:0: [sda] Write Protect is off
[  286.284541] sd 0:0:0:0: [sda] Mode Sense: 00 08 00 00
[  286.284544] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  286.286144] sd 0:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16
).
[  286.286332] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
[  286.286335] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
,SUGGEST_OK
[  286.286338] sd 0:0:0:0: [sda] Use 0xffffffff as device size
[  286.286342] sd 0:0:0:0: [sda] 4294967296 512-byte hardware sectors (2199023 M
B)
[  286.287519] sd 0:0:0:0: [sda] Write Protect is off
[  286.287522] sd 0:0:0:0: [sda] Mode Sense: 00 08 00 00
[  286.287524] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  286.287528]  sda:<6>usb 3-5: reset high speed USB device using ehci_hcd and a
ddress 4
[  348.669109] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  380.966414] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  413.263723] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  445.561037] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  477.858348] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  480.068857] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
,SUGGEST_OK
[  480.068867] end_request: I/O error, dev sda, sector 0
[  480.068872] Buffer I/O error on device sda, logical block 0
[  510.155663] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  542.452976] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  574.750286] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  607.047599] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  639.344908] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  671.642228] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  673.852761] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
,SUGGEST_OK
[  673.852771] end_request: I/O error, dev sda, sector 0
[  673.852776] Buffer I/O error on device sda, logical block 0
[  703.939545] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  736.236847] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  768.534168] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  800.831489] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  833.128787] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  865.426092] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  867.636636] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
,SUGGEST_OK
[  867.636646] end_request: I/O error, dev sda, sector 0
[  867.636651] Buffer I/O error on device sda, logical block 0
[  897.723410] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  933.825573] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  965.431462] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[  996.066152] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1026.700827] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1057.335522] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1057.884468] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
,SUGGEST_OK
[ 1057.884478] end_request: I/O error, dev sda, sector 0
[ 1057.884483] Buffer I/O error on device sda, logical block 0
[ 1087.970202] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1118.604882] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1149.239568] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1179.874263] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1210.508952] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1241.143629] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1241.692589] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK                                                                            ,SUGGEST_OK
[ 1241.692599] end_request: I/O error, dev sda, sector 0
[ 1241.692604] Buffer I/O error on device sda, logical block 0
[ 1241.692837] ldm_validate_partition_table(): Disk read failed.
[ 1271.778312] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1302.412995] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1333.047702] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1363.682368] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1394.317053] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1424.951742] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1425.500834] sd 0:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK                                                                            ,SUGGEST_OK
[ 1425.500844] end_request: I/O error, dev sda, sector 0
[ 1425.500849] Buffer I/O error on device sda, logical block 0
[ 1455.586429] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1486.221132] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1516.855795] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1547.490482] usb 3-5: reset high speed USB device using ehci_hcd and address 4
[ 1578.125168] usb 3-5: reset high speed USB device using ehci_hcd and address 4
uros6@uros6-desktop:~$

---

### Post by samosamo on 2007-10-29
I would say clues to your problem lie here:

[ 286.283031] sd 0:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16
).
[ 286.283329] sd 0:0:0:0: [sda] READ CAPACITY(16) failed

but a quick google on these errors returned nothing interesting.  Your usb disk works in another computer?  Do other usb devices work?

---

### Post by uroskriznar on 2007-10-30
Other devices work in Ubuntu.
But my external disk doesn't work on other computers that are running windows either. Windows say there is a problem with the new hardware that is detected.

---

### Post by gryffus on 2008-06-25
Hi, i have got same problem...

My system is openSUSE 11.0 so this is definetely a hardware error.
I did a "dd if=/filesystem/image of=/dev/sdd" on my TomTom ONE XL GPS, but while dd was running i accidentally unplugged its USB cable...
Since this, partition table is'nt properly recognized...

Maybe some firmware messed up? :confused:

Notice the
Jun 26 02:00:56 gfs-kancl kernel: [ 1757.069254] usb 1-7: reset full speed USB device using ohci_hcd and address 4
and the
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.060943] sd 6:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.061350] sd 6:0:0:0: [sdd] READ CAPACITY(16) failed
lines :popcorn:


My logs:

Jun 26 02:00:49 gfs-kancl kernel: [ 1750.294516] usb 1-7: new full speed USB device using ohci_hcd and address 4
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.450420] usb 1-7: new device found, idVendor=1390, idProduct=0001
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.450431] usb 1-7: new device strings: Mfr=1, Product=2, SerialNumber=3
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.450437] usb 1-7: Product: ONE XL
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.450440] usb 1-7: Manufacturer: TomTom
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.450443] usb 1-7: SerialNumber: L15487K01707
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.451045] usb 1-7: configuration #1 chosen from 1 choice
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.453556] scsi6 : SCSI emulation for USB Mass Storage devices
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.454057] usb-storage: device found at 4
Jun 26 02:00:49 gfs-kancl kernel: [ 1750.454062] usb-storage: waiting for device to settle before scanning
Jun 26 02:00:56 gfs-kancl kernel: [ 1757.069254] usb 1-7: reset full speed USB device using ohci_hcd and address 4
Jun 26 02:01:00 gfs-kancl kernel: [ 1761.271296] scsi 6:0:0:0: Direct-Access     TomTom   ONE XL           707  PQ: 0 ANSI: 2
Jun 26 02:01:00 gfs-kancl kernel: [ 1761.293667] sd 6:0:0:0: [sdd] Attached SCSI removable disk
Jun 26 02:01:00 gfs-kancl kernel: [ 1761.294370] sd 6:0:0:0: Attached scsi generic sg7 type 0
Jun 26 02:01:00 gfs-kancl kernel: [ 1761.295237] usb-storage: device scan complete
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.060943] sd 6:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.061350] sd 6:0:0:0: [sdd] READ CAPACITY(16) failed
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.061356] sd 6:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.061363] sd 6:0:0:0: [sdd] Use 0xffffffff as device size
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.061369] sd 6:0:0:0: [sdd] 4294967296 512-byte hardware sectors (2199023 MB)
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.067946] sd 6:0:0:0: [sdd] Write Protect is off
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.067953] sd 6:0:0:0: [sdd] Mode Sense: 03 00 00 00
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.067957] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.082932] sd 6:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.083050] sd 6:0:0:0: [sdd] READ CAPACITY(16) failed
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.083055] sd 6:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.083061] sd 6:0:0:0: [sdd] Use 0xffffffff as device size
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.083067] sd 6:0:0:0: [sdd] 4294967296 512-byte hardware sectors (2199023 MB)
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.089938] sd 6:0:0:0: [sdd] Write Protect is off
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.089946] sd 6:0:0:0: [sdd] Mode Sense: 03 00 00 00
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.089951] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Jun 26 02:01:01 gfs-kancl kernel: [ 1762.090133]  sdd: unknown partition table


Cya! Gfs

---

### Post by gryffus on 2008-06-25
A few more logs...

gfs-kancl:/home/Gryffus # hexdump -Cv -n 1024 /dev/sdd
00000000  03 00 00 00 00 00 02 00  54 6f 6d 54 6f 6d 20 00  |........TomTom .|
00000010  4f 4e 45 20 58 4c 00 4c  31 35 34 38 37 4b 30 31  |ONE XL.L15487K01|
00000020  37 30 37 00 00 00 00 00  00 00 00 00 00 00 00 00  |707.............|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  3f 1e 03 00 00 00 00 00  |........?.......|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000210  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000220  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000230  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000240  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000250  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000260  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000270  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000280  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000290  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000002a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000002b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000002c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000002d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000002e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000002f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000300  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000310  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000320  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000330  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000340  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000350  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000360  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000370  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000380  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000390  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000003a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000003b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000003c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000003d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000003e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000003f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|



gfs-kancl:/home/Gryffus # cat -n 1 /dev/sdd
cat: 1: není souborem ani adresá&#345;em
     1  TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE XLL15487K01707?U&#65533;TomTom ONE X
.........etc

---

