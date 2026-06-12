---
title: "Crash when reading data from CF card"
date: 2013-01-26
forum: General Help
---

### Post by JonatanK on 2013-01-26
Hi!

I have a problem with reading photos from my camera. Whenever I connect the camera directly, or the CF card with a card reader, I can open it, copy a few files, and then it crashes.

I wonder whether the card is just too big (32Gb SanDisk 90Mb/s), or what is the problem?
I had no problems earlier with the same computer, running Windows Vista.
I use only Ubuntu (12.10) now, and I would be glad to work with my photos on it.

What can be the cause? How to fix this?
I would appreciate any help.

Cheers!
Jonatan

---

### Post by jorok_tupur on 2013-01-27
Can you post the relevant content of /var/log/syslog ?

---

### Post by tgalati4 on 2013-01-27
Open a terminal, plug the card or camera in and post the output of:

```
dmesg | tail -50
```

Could be timing issues, could be a cable issue, could be the firmware on the card reader.

---

### Post by JonatanK on 2013-02-09
Sorry for not responding for so long. I tried various cables, and both from a card reader and directly from the camera. From a card reader does not even mount (the same card reader works on windows).

That's the output:
```
dmesg | tail -50
[ 1640.811602] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[ 1640.812614] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1640.812623] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1640.820483] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1640.820494] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1640.862907]  sdb: sdb1
[ 1640.867345] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1640.867353] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1640.867358] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1646.252033] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:13:5f:1e:2a:c0:08:00 SRC=130.88.185.250 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=18180 PROTO=2 
[ 1655.459371] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:00:50:b6:4f:94:1f:86:dd SRC=fe80:0000:0000:0000:0250:b6ff:fe4f:941f DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=271 TC=0 HOPLIMIT=255 FLOWLBL=0 FRAG:1232 ID:2d4055e5 PROTO=UDP 
[ 1668.541171] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:36:02:29:08:00 SRC=130.88.186.11 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=5613 PROTO=UDP SPT=57227 DPT=8612 LEN=24 
[ 1686.300249] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:70:cd:60:80:0f:5c:08:00 SRC=130.88.186.174 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=41416 PROTO=UDP SPT=62624 DPT=8612 LEN=24 
[ 1706.294215] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:bc:c8:8e:7e:f6:08:00 SRC=130.88.85.26 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=61845 PROTO=UDP SPT=57118 DPT=8612 LEN=24 
[ 1726.652777] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=37723 PROTO=UDP SPT=49473 DPT=8612 LEN=24 
[ 1747.909174] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=11660 PROTO=UDP SPT=56604 DPT=8612 LEN=24 
[ 1766.311305] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:13:5f:1e:2a:c0:08:00 SRC=130.88.185.250 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=24127 PROTO=2 
[ 1786.314451] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:2a:14:27:e3:0f:08:00 SRC=130.88.85.101 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=58405 PROTO=UDP SPT=55587 DPT=8612 LEN=24 
[ 1804.823430] usb 2-2: USB disconnect, device number 2
[ 1805.064121] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1806.522591] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:2a:14:25:e1:95:08:00 SRC=130.88.187.231 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=17000 PROTO=UDP SPT=60295 DPT=8612 LEN=24 
[ 1816.748191] usb 2-2: new high-speed USB device number 4 using ehci_hcd
[ 1817.287934] usb 2-2: New USB device found, idVendor=0bda, idProduct=0151
[ 1817.287944] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1817.287950] usb 2-2: Product: USB2.0-CRW
[ 1817.287955] usb 2-2: Manufacturer: Generic
[ 1817.287960] usb 2-2: SerialNumber: 20060413092100000
[ 1817.292461] scsi6 : usb-storage 2-2:1.0
[ 1818.298753] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[ 1818.305231] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[ 1818.311622] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[ 1818.318000] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[ 1818.319129] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1818.319659] sd 6:0:0:1: Attached scsi generic sg3 type 0
[ 1818.327459] sd 6:0:0:2: Attached scsi generic sg4 type 0
[ 1818.327798] sd 6:0:0:3: Attached scsi generic sg5 type 0
[ 1818.787686] sd 6:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 1818.789671] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[ 1818.790888] sd 6:0:0:0: [sdb] Write Protect is off
[ 1818.790895] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1818.793050] sd 6:0:0:0: [sdb] No Caching mode page present
[ 1818.793057] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1818.793803] sd 6:0:0:3: [sde] Attached SCSI removable disk
[ 1818.795977] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[ 1818.802173] sd 6:0:0:0: [sdb] No Caching mode page present
[ 1818.802181] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1818.844619]  sdb: sdb1
[ 1818.850430] sd 6:0:0:0: [sdb] No Caching mode page present
[ 1818.850439] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1818.850445] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by JonatanK on 2013-02-09
And that's the output with the camera directly (the las one was with the card reader):
```
dmesg | tail -50
[ 1804.823430] usb 2-2: USB disconnect, device number 2
[ 1805.064121] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1806.522591] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:2a:14:25:e1:95:08:00 SRC=130.88.187.231 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=17000 PROTO=UDP SPT=60295 DPT=8612 LEN=24 
[ 1816.748191] usb 2-2: new high-speed USB device number 4 using ehci_hcd
[ 1817.287934] usb 2-2: New USB device found, idVendor=0bda, idProduct=0151
[ 1817.287944] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1817.287950] usb 2-2: Product: USB2.0-CRW
[ 1817.287955] usb 2-2: Manufacturer: Generic
[ 1817.287960] usb 2-2: SerialNumber: 20060413092100000
[ 1817.292461] scsi6 : usb-storage 2-2:1.0
[ 1818.298753] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[ 1818.305231] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[ 1818.311622] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[ 1818.318000] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[ 1818.319129] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1818.319659] sd 6:0:0:1: Attached scsi generic sg3 type 0
[ 1818.327459] sd 6:0:0:2: Attached scsi generic sg4 type 0
[ 1818.327798] sd 6:0:0:3: Attached scsi generic sg5 type 0
[ 1818.787686] sd 6:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 1818.789671] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[ 1818.790888] sd 6:0:0:0: [sdb] Write Protect is off
[ 1818.790895] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1818.793050] sd 6:0:0:0: [sdb] No Caching mode page present
[ 1818.793057] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1818.793803] sd 6:0:0:3: [sde] Attached SCSI removable disk
[ 1818.795977] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[ 1818.802173] sd 6:0:0:0: [sdb] No Caching mode page present
[ 1818.802181] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1818.844619]  sdb: sdb1
[ 1818.850430] sd 6:0:0:0: [sdb] No Caching mode page present
[ 1818.850439] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1818.850445] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1826.250903] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:13:5f:1e:2a:c0:08:00 SRC=130.88.185.250 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=60235 PROTO=2 
[ 1847.099669] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=64137 PROTO=UDP SPT=59438 DPT=8612 LEN=24 
[ 1868.355617] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=17390 PROTO=UDP SPT=58483 DPT=8612 LEN=24 
[ 1886.253168] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:13:5f:1e:2a:c0:08:00 SRC=130.88.185.250 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=26121 PROTO=2 
[ 1906.711395] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:2a:14:27:e3:0f:08:00 SRC=130.88.85.101 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=28881 PROTO=UDP SPT=59011 DPT=8612 LEN=24 
[ 1907.384594] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:3c:07:54:05:8d:88:86:dd SRC=fe80:0000:0000:0000:3e07:54ff:fe05:8d88 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=118 TC=0 HOPLIMIT=255 FLOWLBL=0 FRAG:1232 ID:3e979d76 PROTO=UDP 
[ 1926.938927] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:2a:14:25:e1:95:08:00 SRC=130.88.187.231 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=47881 PROTO=UDP SPT=55718 DPT=8612 LEN=24 
[ 1946.291758] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=1656 PROTO=UDP SPT=58199 DPT=8612 LEN=24 
[ 1964.024086] usb 2-2: USB disconnect, device number 4
[ 1967.542496] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=8484 PROTO=UDP SPT=50366 DPT=8612 LEN=24 
[ 1967.826931] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:40:6c:8f:35:a9:eb:86:dd SRC=fe80:0000:0000:0000:426c:8fff:fe35:a9eb DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=221 TC=0 HOPLIMIT=255 FLOWLBL=0 FRAG:1232 ID:ceaa18a4 PROTO=UDP 
[ 1979.867846] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:40:6c:8f:35:a9:eb:86:dd SRC=fe80:0000:0000:0000:426c:8fff:fe35:a9eb DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=74 TC=0 HOPLIMIT=255 FLOWLBL=0 FRAG:1232 ID:9c8b38b3 PROTO=UDP 
[ 1988.796678] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:6c:8f:3d:47:30:08:00 SRC=130.88.186.205 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=49961 PROTO=UDP SPT=57635 DPT=8612 LEN=24 
[ 1989.532175] usb 2-3: new high-speed USB device number 5 using ehci_hcd
[ 1989.671671] usb 2-3: New USB device found, idVendor=04a9, idProduct=3199
[ 1989.671681] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1989.671687] usb 2-3: Product: Canon Digital Camera
[ 1989.671693] usb 2-3: Manufacturer: Canon Inc.

```

---

### Post by tgalati4 on 2013-02-09
I presume that the card reader came with a Windows driver.  It appears that the card reader generic module is having problems with your card.  Either due to size of the card or because it can't detect any caching mode, so it just does blind writes until the card or the reader barfs.

You want to run the dmesg command right after plugging in the card and trying to write to it.  You may have to change the 50 to 100 to get 100 lines of output.  Look for read, write, or access errors.

It's a sad fact that some hardware is poorly supported in linux.  You can either look for a newer/different card reader--perhaps one dedicated to CF cards as opposed to a multi-reader.  Do you have any HP printers with CF card readers built in?  Have you tried them?

Finding a work-around is the first step.  Then finding the specific issue causing your problem won't be as pressing.

Does your reader or camera connection work with smaller cards?  Do you have any other cameras with CF cards to connect?

---

