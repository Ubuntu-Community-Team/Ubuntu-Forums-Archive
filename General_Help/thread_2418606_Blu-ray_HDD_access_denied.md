---
title: "Blu-ray HDD access denied"
date: 2019-05-08
forum: General Help
---

### Post by xtrodinarry on 2019-05-08
Hello,
I have plugged an external HDD to my laptop. It is from an LG Blu-ray  player and my guess is that the drive is encrypted somehow. I am really  new to Ubuntu so I do not really know how to get permission the drive.  What I know so far is that I typed dmesg to the terminal and got this  back from the drive:

Device= 1.00
[  120.004869] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[  120.004871] usb 1-3: Product: USB to ATA/ATAPI Bridge
[  120.004872] usb 1-3: Manufacturer: JMicron
[  120.004874] usb 1-3: SerialNumber: B2211474BFFF
[  120.006042] usb-storage 1-3:1.0: USB Mass Storage device detected
[  120.006153] scsi host5: usb-storage 1-3:1.0
[  121.024382] scsi 5:0:0:0: Direct-Access     Hitachi  HTS541680J9SA00       PQ: 0 ANSI: 2 CCS
[  121.024691] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  121.251180] sd 5:0:0:0: [sdd] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[  121.251442] sd 5:0:0:0: [sdd] Write Protect is off
[  121.251445] sd 5:0:0:0: [sdd] Mode Sense: 34 00 00 00
[  121.251683] sd 5:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  121.253080] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  121.253084] sd 5:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[  121.253088] sd 5:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[  121.253092] sd 5:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[  121.253095] print_req_error: critical medium error, dev sdd, sector 0
[  121.253100] Buffer I/O error on dev sdd, logical block 0, async page read
[  121.254834] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  121.254839] sd 5:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[  121.254842] sd 5:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[  121.254846] sd 5:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[  121.254849] print_req_error: critical medium error, dev sdd, sector 0
[  121.254855] Buffer I/O error on dev sdd, logical block 0, async page read
[  121.255264] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  121.255267] sd 5:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[  121.255270] sd 5:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[  121.255273] sd 5:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00

The list goes on but the thread would be really long so I hope this is enough to know what could be the problem.

I do not really know what this info means so I would appreciate any kind of help :D

---

### Post by SeijiSensei on 2019-05-08
Does it have a disk inside? If so, what happens if you remove it? A "read error" suggests the device is having problems reading a medium. 

What if you load a different disk, perhaps a blank one?

If it's a commercial disk with a movie or other content, it's likely protected and can't be read normally.

---

