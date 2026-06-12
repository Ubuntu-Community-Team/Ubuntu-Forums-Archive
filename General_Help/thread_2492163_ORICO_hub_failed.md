---
title: "ORICO hub failed"
date: 2023-11-01
forum: General Help
---

### Post by amnamn on 2023-11-01
Hi there, I bought  ORICO 6228US3-C dock and it fails when I copy data from or to it. this is dmesg output
```
GPT: Use GNU Parted to correct GPT errors.
[43849.157633]  sda: sda1
[43849.158437] sd 0:0:0:0: [sda] Attached SCSI disk
[43850.134417] usb 4-1: USB disconnect, device number 21
[43850.146392] blk_print_req_error: 3472 callbacks suppressed
[43850.146400] device offline error, dev sda, sector 2048 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 2
[43850.146450] ntfs3: sda1: failed to read volume at offset 0x0
[43850.218431] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[43850.462375] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[43850.774501] usb 4-1: new SuperSpeed USB device number 22 using xhci_hcd
[43850.795379] usb 4-1: New USB device found, idVendor=152d, idProduct=0565, bcdDevice= 0.09
[43850.795392] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[43850.795397] usb 4-1: Product: JMS56x Series
[43850.795400] usb 4-1: Manufacturer: JMicron
[43850.795403] usb 4-1: SerialNumber: RANDOM__22374CDBF833
[43850.801705] scsi host0: uas
[43850.802480] scsi 0:0:0:0: Direct-Access     TOSHIBA  MQ01ABD100       0009 PQ: 0 ANSI: 6
[43850.805435] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[43850.806085] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[43850.806372] sd 0:0:0:0: [sda] Write Protect is off
[43850.806378] sd 0:0:0:0: [sda] Mode Sense: 67 00 10 08
[43850.806795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[43850.807026] sd 0:0:0:0: [sda] Preferred minimum I/O size 4096 bytes
[43850.807031] sd 0:0:0:0: [sda] Optimal transfer size 33553920 bytes not a multiple of preferred minimum block size (4096 bytes)

```

```

GPT: Use GNU Parted to correct GPT errors.
[43868.836962]  sda: sda1
[43868.837255] sd 0:0:0:0: [sda] Attached SCSI disk
[43869.571619] ntfs3: sda1: volume is dirty and "force" flag is not set!
[43870.258532] usb 4-1: USB disconnect, device number 25
[43870.258914] sd 0:0:0:0: [sda] tag#4 uas_zap_pending 0 uas-tag 1 inflight: CMD 
[43870.258927] sd 0:0:0:0: [sda] tag#4 CDB: Read(10) 28 00 00 00 0a 90 00 00 08 00
[43870.258938] sd 0:0:0:0: [sda] tag#18 uas_zap_pending 0 uas-tag 2 inflight: CMD 
[43870.258943] sd 0:0:0:0: [sda] tag#18 CDB: Read(10) 28 00 74 70 67 f0 00 00 08 00
[43870.259006] sd 0:0:0:0: [sda] tag#4 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[43870.259012] sd 0:0:0:0: [sda] tag#4 CDB: Read(10) 28 00 00 00 0a 90 00 00 08 00
[43870.259016] I/O error, dev sda, sector 2704 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 2
[43870.259058] sd 0:0:0:0: [sda] tag#18 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[43870.259064] sd 0:0:0:0: [sda] tag#18 CDB: Read(10) 28 00 74 70 67 f0 00 00 08 00
[43870.259067] I/O error, dev sda, sector 1953523696 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 2
[43870.259215] device offline error, dev sda, sector 1953523696 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 2
[43870.259241] buffer_io_error: 142097 callbacks suppressed
[43870.259247] Buffer I/O error on dev sda1, logical block 244190206, async page read
[43870.259278] device offline error, dev sda, sector 2704 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 2
[43870.259288] Buffer I/O error on dev sda1, logical block 82, async page read
[43870.260974] device offline error, dev sda, sector 2712 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 2
[43870.261059] device offline error, dev sda, sector 2712 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 2
[43870.261075] Buffer I/O error on dev sda1, logical block 83, async page read
[43870.263212] device offline error, dev sda, sector 244192264 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 2
[43870.263275] device offline error, dev sda, sector 244192264 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 2
[43870.263286] Buffer I/O error on dev sda1, logical block 30523777, async page read
[43870.264484] Buffer I/O error on dev sda1, logical block 30870104, async page read
[43870.334349] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[43870.586346] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK

```


can anyone explain to me what the problem is?

---

### Post by MAFoElffen on 2023-11-03
What is the output of 
```

lsusb -tvvv
sudo sgdisk /dev/sda

```
posted within CODE Tags.

---

