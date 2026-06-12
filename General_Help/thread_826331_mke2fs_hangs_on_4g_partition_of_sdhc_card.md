---
title: "mke2fs hangs on 4g partition of sdhc card"
date: 2008-06-11
forum: General Help
---

### Post by stairwayoflight on 2008-06-11
Hello,

I have a an asus eeepc with sdhc reader. While trying to install ubuntu onto my transcend 16gb sdhc card, the installer just hangs. That is, I was trying to install ubuntu on a / ext2 partition on the first 4gb of the card.

I booted another system on it, and tried to create the partitions manually. fdisk seemed to work ok. But when I did:

```
mke2fs /dev/sdc1
```

everything rolled along ok until it printed:

```
Writing inode tables: done                            
Writing superblocks and filesystem accounting information:
```
At that point it seemed to hang. I waited some time, although probably less than an hour. I am hoping my card isn't dead, but as it is my only sdhc reader I can't tell. Before this it was brand new. :-(

---

### Post by stairwayoflight on 2008-06-11
Hmm,

mke2fs seemed to work ok, less than 30 seconds for a 8gb partition.

---

### Post by stairwayoflight on 2008-06-11
Ok, I am getting some errors. Does this mean the card is finished?

```
[  395.708000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  494.428000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  525.096000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  555.772000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  586.436000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  617.100000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  647.764000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  678.428000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  709.092000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  709.644000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  709.644000] end_request: I/O error, dev sdb, sector 63
[  709.644000] Buffer I/O error on device sdb1, logical block 0
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 1
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 2
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 3
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 4
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 5
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 6
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 7
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 8
[  709.644000] lost page write due to I/O error on sdb1
[  709.644000] Buffer I/O error on device sdb1, logical block 9
[  709.644000] lost page write due to I/O error on sdb1
[  739.760000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  770.424000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  801.088000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  831.760000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  862.432000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  893.096000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  923.760000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  954.436000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[  985.140000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1015.816000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1046.484000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1077.148000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1107.824000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1138.512000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1169.180000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1199.852000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1230.528000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1261.192000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1291.852000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1322.516000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1353.180000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1383.844000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1414.512000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1445.180000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1475.848000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1506.512000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1537.184000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1567.864000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1598.528000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1629.200000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1659.864000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1690.532000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
[ 1721.204000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
```

I noticed the partion I was copying from and the target were *exactly* the same size, so instead of cp I did 'dd if=/dev/sdc1 of=/dev/sdb1'. Thats when all these errors showed up in dmesg.

---

### Post by stairwayoflight on 2008-06-12
Just thought I'd mention I poked around the eeeuser.com forums, and found out some people had sdhc woes until changing "finished" to "not finished" in the system bios. Mine didn't say "not finished" but "start" so I changed it anyways. After this, the dd operation seemed to work alright, but I wasn't sure 'cause wmii crashed.

On a side note, the ubuntu system I dd'd to the drive did boot, albeit slowly. Kept getting grub error 15 until manually setting it up from the grub console instead of grub-install.

Unfortunately I am still getting read errors though.

---

