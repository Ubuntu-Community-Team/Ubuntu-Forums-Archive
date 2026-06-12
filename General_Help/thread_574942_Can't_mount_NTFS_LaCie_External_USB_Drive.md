---
title: "Can't mount NTFS LaCie External USB Drive"
date: 2007-10-13
forum: General Help
---

### Post by jilagan on 2007-10-13
This thing has been mind boggling...

Two weeks ago, I had no problems mounting my LaCie 500MB External USB drive through ntfs-3g. For some reason, I now get the following error when mounting:

ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error

I tried booting up Windows XP and the drive is mounted fine. I did a chkdsk /f and no errors were found.

When running dmesg, I get these strange error messages:

[  122.620000] Initializing USB Mass Storage driver...
[  122.620000] scsi2 : SCSI emulation for USB Mass Storage devices
[  122.620000] usb-storage: device found at 4
[  122.620000] usbcore: registered new interface driver usb-storage
[  122.620000] USB Mass Storage support registered.
[  122.620000] usb-storage: waiting for device to settle before scanning
[  127.620000] usb-storage: device scan complete
[  127.620000] scsi 2:0:0:0: Direct-Access     LaCie    Big Disk G467         PQ: 0 ANSI: 4
[  127.640000] sd 2:0:0:0: [sdb] 980469503 512-byte hardware sectors (502000 MB)
[  127.640000] sd 2:0:0:0: [sdb] Write Protect is off
[  127.640000] sd 2:0:0:0: [sdb] Mode Sense: 11 00 00 00
[  127.640000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  127.644000] sd 2:0:0:0: [sdb] 980469503 512-byte hardware sectors (502000 MB)
[  127.644000] sd 2:0:0:0: [sdb] Write Protect is off
[  127.644000] sd 2:0:0:0: [sdb] Mode Sense: 11 00 00 00
[  127.644000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  127.644000]  sdb: sdb1
[  127.664000] sd 2:0:0:0: [sdb] Attached SCSI disk
[  127.664000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  128.312000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  128.312000] end_request: I/O error, dev sdb, sector 490234687
[  128.312000] Buffer I/O error on device sdb1, logical block 490234624
[  128.312000] Buffer I/O error on device sdb1, logical block 490234625
[  128.312000] Buffer I/O error on device sdb1, logical block 490234626
[  128.312000] Buffer I/O error on device sdb1, logical block 490234627
[  128.312000] Buffer I/O error on device sdb1, logical block 490234628
[  128.312000] Buffer I/O error on device sdb1, logical block 490234629
[  128.312000] Buffer I/O error on device sdb1, logical block 490234630
[  128.312000] Buffer I/O error on device sdb1, logical block 490234631
[  128.312000] Buffer I/O error on device sdb1, logical block 490234632
[  128.312000] Buffer I/O error on device sdb1, logical block 490234633
[  791.420000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  791.420000] end_request: I/O error, dev sdb, sector 490234687
[  791.420000] printk: 118 messages suppressed.

Please help! Thanks.

---

### Post by jilagan on 2007-10-13
Sorry, I have Ubuntu Gutsy Gibbon Beta (7.10) installed, though it's been updated daily since two weeks ago. The ntfs-3g version installed is 1:1.913-2ubuntu1.

---

### Post by ltcmdata on 2007-10-24
funny, have the same problem with an ipod here.

---

### Post by Halfling Rogue on 2007-10-24
Same (or similar) problem with a WD ext HD, only mine won't mount on Windows either, and I get the error during initial boot.

---

### Post by z987k on 2007-10-27
I'm also getting this error with a Maxtor external HDD.  It's formated NTFS.  Running 7.10
```
root@linux:~# mount -t ntfs-3g /dev/sdb1 /media/dan -O ro
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
Unmounting /dev/sdb1 (Maxtor )

```

---

### Post by Halfling Rogue on 2007-10-27
Isn't there a patch for this anywhere?

---

### Post by szaka on 2007-10-29
The below kernel messages clearly mean hardware (disk) error:
[i]
Buffer I/O error on device sdb1, logical block XXXXXXXXXXX
[/i]
However it's somehow unprobable that so many peope would have the same error with so many disks. This looks more like an Ubuntu kernel device driver bug which was introduced recently.

Note, that NTFS-3G absolutely can not do anything about this problem. It asks the kernel and the hardware that "give me this data" however the reply is not the data but an "error" what NTFS-3G reports to the user.

Please submit an Ubuntu bug report for the kernel for this issue with the exact error messages and hardware info.

---

### Post by Halfling Rogue on 2007-10-29
Some of us are using Gutsy, some Dapper, and some Feisty, so should we report a bug for each?

---

### Post by szaka on 2007-10-29
> **Halfling Rogue said:**
> Some of us are using Gutsy, some Dapper, and some Feisty, so should we report a bug for each?
Of course if you have exactly the same unable to read disk kernel errors.

---

### Post by etlpkby on 2008-04-03
Just want to mention this regarding LACIE USB disks - of which I have 500Mb USB2.0 version.

If you (for some reason) disconnect the power or usb cable when it is mounted - it will not remount - the little blue light will flash continuously - but it will not mount. This is what I have to do to fix it.

1. Switch off the Lacie disk. 
2. Disconnect Power
3. Remove USB cable from system.
4. Reboot 
5. Reconnect power cable
6. Attach USB cable.

Item (4) is recommended, but you can try and skip - your mileage will vary :-k

I am running Ubuntu 8.04 (Heron Alpha6 on AMD64 - but this problem happened on Gusty 7.10 and FC4 before that.

Patrick/

---

