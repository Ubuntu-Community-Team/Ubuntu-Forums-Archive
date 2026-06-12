---
title: "Unclaen USB unmount"
date: 2013-05-05
forum: General Help
---

### Post by swat-leader on 2013-05-05
Hi all,
I was using ubuntu instaledl on a usb sitck. long story short i was copying files to a differnt USB stick when ubuntu locked up. After that the USB is no longer working. I tried Gparted on knopix and it doesnt show. but if type dmsg here is the output.

[  310.992483] usb-storage: waiting for device to settle before scanning
[  310.992681] usb 1-5: New USB device found, idVendor=0951, idProduct=1653
[  310.992685] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  310.992688] usb 1-5: Product: DT 100 G2
[  310.992690] usb 1-5: Manufacturer: Kingston
[  310.992693] usb 1-5: SerialNumber: 001CC0EC34E1FC61171524F3
[  316.079407] scsi 6:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 4 CCS
[  316.082484] sd 6:0:0:0: [sde] READ CAPACITY failed
[  316.082487] sd 6:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  316.082493] sd 6:0:0:0: [sde] Sense Key : Unit Attention [current] 
[  316.082498] sd 6:0:0:0: [sde] Add. Sense: Not ready to ready change, medium may have changed
[  316.082980] sd 6:0:0:0: [sde] Write Protect is off
[  316.082984] sd 6:0:0:0: [sde] Mode Sense: 45 00 00 00
[  316.082987] sd 6:0:0:0: [sde] Assuming drive cache: write through
[  316.083107] sd 6:0:0:0: [sde] Attached SCSI removable disk
[  316.083257] sd 6:0:0:0: Attached scsi generic sg4 type 0
[  316.083715] usb-storage: device scan complete
[  415.346023] usb 1-5: USB disconnect, address 3
[  431.363359] usb 2-3: new high speed USB device using ehci_hcd and address 9
[  431.491584] usb 2-3: configuration #1 chosen from 1 choice
[  431.492159] scsi7 : SCSI emulation for USB Mass Storage devices
[  431.492794] usb 2-3: New USB device found, idVendor=0951, idProduct=1653
[  431.492800] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  431.492805] usb 2-3: Product: DT 100 G2
[  431.492809] usb 2-3: Manufacturer: Kingston
[  431.492813] usb 2-3: SerialNumber: 001CC0EC34E1FC61171524F3
[  431.492820] usb-storage: device found at 9
[  431.492824] usb-storage: waiting for device to settle before scanning
[  436.579393] scsi 7:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 4 CCS
[  436.582359] sd 7:0:0:0: [sde] READ CAPACITY failed
[  436.582365] sd 7:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  436.582371] sd 7:0:0:0: [sde] Sense Key : Unit Attention [current] 
[  436.582378] sd 7:0:0:0: [sde] Add. Sense: Not ready to ready change, medium may have changed
[  436.582857] sd 7:0:0:0: [sde] Write Protect is off
[  436.582863] sd 7:0:0:0: [sde] Mode Sense: 45 00 00 00
[  436.582867] sd 7:0:0:0: [sde] Assuming drive cache: write through
[  436.583016] sd 7:0:0:0: [sde] Attached SCSI removable disk
[  436.583173] sd 7:0:0:0: Attached scsi generic sg4 type 0
[  436.583545] usb-storage: device scan complete
[  798.955925] usb 2-3: USB disconnect, address 9
[  801.830614] usb 2-3: new high speed USB device using ehci_hcd and address 10
[  801.958110] usb 2-3: configuration #1 chosen from 1 choice
[  801.958851] scsi8 : SCSI emulation for USB Mass Storage devices
[  801.959361] usb-storage: device found at 10
[  801.959364] usb-storage: waiting for device to settle before scanning
[  801.959591] usb 2-3: New USB device found, idVendor=0951, idProduct=1653
[  801.959596] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  801.959601] usb 2-3: Product: DT 100 G2
[  801.959604] usb 2-3: Manufacturer: Kingston
[  801.959608] usb 2-3: SerialNumber: 001CC0EC34E1FC61171524F3
[  807.046204] scsi 8:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 4 CCS
[  807.049274] sd 8:0:0:0: [sde] READ CAPACITY failed
[  807.049278] sd 8:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  807.049284] sd 8:0:0:0: [sde] Sense Key : Unit Attention [current] 
[  807.049289] sd 8:0:0:0: [sde] Add. Sense: Not ready to ready change, medium may have changed
[  807.049768] sd 8:0:0:0: [sde] Write Protect is off
[  807.049772] sd 8:0:0:0: [sde] Mode Sense: 45 00 00 00
[  807.049775] sd 8:0:0:0: [sde] Assuming drive cache: write through
[  807.049875] sd 8:0:0:0: [sde] Attached SCSI removable disk
[  807.050005] sd 8:0:0:0: Attached scsi generic sg4 type 0
[  807.050376] usb-storage: device scan complete
[ 1395.262017] usb 2-3: USB disconnect, address 10
[ 1397.613258] usb 2-3: new high speed USB device using ehci_hcd and address 11
[ 1397.741002] usb 2-3: configuration #1 chosen from 1 choice
[ 1397.741274] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1397.741389] usb-storage: device found at 11
[ 1397.741392] usb-storage: waiting for device to settle before scanning
[ 1397.741659] usb 2-3: New USB device found, idVendor=0951, idProduct=1653
[ 1397.741664] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1397.741669] usb 2-3: Product: DT 100 G2
[ 1397.741672] usb 2-3: Manufacturer: Kingston
[ 1397.741676] usb 2-3: SerialNumber: 001CC0EC34E1FC61171524F3
[ 1402.829295] scsi 9:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 4 CCS
[ 1402.832341] sd 9:0:0:0: [sde] READ CAPACITY failed
[ 1402.832345] sd 9:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1402.832350] sd 9:0:0:0: [sde] Sense Key : Unit Attention [current] 
[ 1402.832355] sd 9:0:0:0: [sde] Add. Sense: Not ready to ready change, medium may have changed
[ 1402.832837] sd 9:0:0:0: [sde] Write Protect is off
[ 1402.832840] sd 9:0:0:0: [sde] Mode Sense: 45 00 00 00
[ 1402.832843] sd 9:0:0:0: [sde] Assuming drive cache: write through
[ 1402.832959] sd 9:0:0:0: [sde] Attached SCSI removable disk
[ 1402.833113] sd 9:0:0:0: Attached scsi generic sg4 type 0
[ 1402.833816] usb-storage: device scan complete

So then I tired fdisk -l /dev/sde (following a websites ideas) but i had no message after.

so now what ?? is there anything i can try for is that USB off to the bin ??

Cheers

Shane

---

