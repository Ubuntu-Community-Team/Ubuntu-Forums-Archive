---
title: "Cannot mount External USB HD."
date: 2014-04-26
forum: General Help
---

### Post by buntu_hugenewbie11 on 2014-04-26
So I have tried mounting my external hard drive using mount-a.
There are two partitions and it seems to mount one but not the other and then I cannot read it anyways. 
Even through the command line it gives me an error.
I was able to read it before upgrading to 12.04 (64 bit).
And I just checked it on a Windows machine today and it works.
But for some reason in Linux I cannot access it.
Here is my lsusb and dmesg:

root@myob11:/media/PrimaryForBackUps# dmesg
[30082.734546] usb 2-1.4: new high-speed USB device number 17 using ehci_hcd
[30082.828757] scsi9 : usb-storage 2-1.4:1.0
[30083.826350] scsi 9:0:0:0: Direct-Access     WD       My Passport 0740 1003 PQ: 0 ANSI: 6
[30083.826870] scsi 9:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
[30083.828595] sd 9:0:0:0: Attached scsi generic sg2 type 0
[30083.828869] ses 9:0:0:1: Attached Enclosure device
[30083.829031] ses 9:0:0:1: Attached scsi generic sg3 type 13
[30090.522957] sd 9:0:0:0: [sdc] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
[30090.524567] sd 9:0:0:0: [sdc] Write Protect is off
[30090.524577] sd 9:0:0:0: [sdc] Mode Sense: 47 00 10 08
[30090.525877] sd 9:0:0:0: [sdc] No Caching mode page found
[30090.525884] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[30090.530371] sd 9:0:0:0: [sdc] No Caching mode page found
[30090.530378] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[30090.543992]  sdc: sdc1 sdc2
[30090.549142] sd 9:0:0:0: [sdc] No Caching mode page found
[30090.549149] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[30090.549155] sd 9:0:0:0: [sdc] Attached SCSI disk
[30105.457970] Buffer I/O error on device sdb1, logical block 16122739
[30105.638947] Buffer I/O error on device sdb1, logical block 16122739
[30222.797340] Buffer I/O error on device sdb1, logical block 16122739
[30222.842075] Buffer I/O error on device sdb1, logical block 16122739
[30223.050398] Buffer I/O error on device sdb1, logical block 16122739
[30223.181083] Buffer I/O error on device sdb1, logical block 16122739
[30256.032774] Buffer I/O error on device sdb1, logical block 16122739
root@myob11:/media/PrimaryForBackUps# ls
ls: reading directory .: Input/output error
root@myob11:/media/PrimaryForBackUps# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 005: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
Bus 002 Device 003: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 005: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 001 Device 006: ID 046d:c529 Logitech, Inc. diNovo Keyboard for notebooks
Bus 002 Device 017: ID 1058:0740 Western Digital Technologies, Inc. My Passport 1TB

---

### Post by tfrue on 2014-04-27
Here is something to try.

It looks like the drive you are tying to mount is /dev/sdc, so let's try and mount that device. It's also assumed that there is only one primary partition on the drive.

First, you need to make a mount point, type (Be sure to use any name you want were it says test):
```
sudo mkdir /media/test
```
That will make a directory under /media to mount to. Next, let's mount the connected drive (/dev/sdc1) to the newly created mount point. Type:
```
sudo mount -t autofs -o defaults /dev/sdc1 /media/test
```
That will mount the device /sdc1 (Your external drive) to the mount point /media/test with an auto detect of the FS and default options on the drive.
If you are wanting this device to auto mount at boot, you will need to take a look at this article.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by buntu_hugenewbie11 on 2014-04-28
II tried your command. Of
 sudo mount -t autofs -o defaults /dev/sdc1 /media/test
autofs gave me unknown filesystem type so I switched it to auto.
The hard drive made noise beeped, the command hung for 2 minutes and then nothing.
I actually have 2 partitions on the drive and have two separate mount points.
I used to have it automated before reinstalling 12.04 on my system. I have no idea why this is happening.
It seems that the connection keeps getting reset. The drive mounts and I can see the first folder contents in Dolphin and then it hangs and I can't go further.
The format is NTFS but it seems that ehci_hcd keeps resetting the connection to the external hard drive.
Below is the dmesg:
dmesg
root@myob11:/media/PrimaryForBackUps# dmesg
[157635.466542] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[157742.181756] ieee80211 phy0: START: tid 1 is not agg'able
[157744.419879] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[157857.337375] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[157958.170226] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[158035.740901] ieee80211 phy0: START: tid 1 is not agg'able
[158134.004594] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[158144.158955] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[158144.242966] usb 2-1.1: device descriptor read/64, error -71
[158144.430703] usb 2-1.1: device descriptor read/64, error -71
[158144.606444] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[158144.690505] usb 2-1.1: device descriptor read/64, error -71
[158144.878138] usb 2-1.1: device descriptor read/64, error -71
[158145.054162] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[158145.469405] usb 2-1.1: device not accepting address 22, error -71
[158145.541442] usb 2-1.1: reset high-speed USB device number 22 using ehci_hcd
[158145.957046] usb 2-1.1: device not accepting address 22, error -71
[158145.957544] sd 12:0:0:0: Device offlined - not ready after error recovery
[158145.957566] sd 12:0:0:0: [sdc] Unhandled error code
[158145.957569] sd 12:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[158145.957573] sd 12:0:0:0: [sdc] CDB: Read(10): 28 00 6f 14 75 0f 00 00 80 00
[158145.957582] end_request: I/O error, dev sdc, sector 1863611663
[158145.957586] Buffer I/O error on device sdc1, logical block 117751351
[158145.957591] Buffer I/O error on device sdc1, logical block 117751352
[158145.957594] Buffer I/O error on device sdc1, logical block 117751353
[158145.957598] Buffer I/O error on device sdc1, logical block 117751354
[158145.957601] Buffer I/O error on device sdc1, logical block 117751355
[158145.957604] Buffer I/O error on device sdc1, logical block 117751356
[158145.957607] Buffer I/O error on device sdc1, logical block 117751357
[158145.957610] Buffer I/O error on device sdc1, logical block 117751358
[158145.957613] Buffer I/O error on device sdc1, logical block 117751359
[158145.957628] sd 12:0:0:0: rejecting I/O to offline device
[158145.957632] sd 12:0:0:0: [sdc] killing request
[158145.957646] sd 12:0:0:0: [sdc] Unhandled error code
[158145.957649] sd 12:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[158145.957652] sd 12:0:0:0: [sdc] CDB: Read(10): 28 00 36 f3 ad 57 00 00 08 00
[158145.957661] end_request: I/O error, dev sdc, sector 921939287
[158145.957715] sd 12:0:0:0: rejecting I/O to offline device
[158145.957721] usb 2-1.1: USB disconnect, device number 22
[158146.033040] usb 2-1.1: new high-speed USB device number 23 using ehci_hcd
[158146.117011] usb 2-1.1: device descriptor read/64, error -71
[158146.308795] usb 2-1.1: device descriptor read/64, error -71
[158146.484619] usb 2-1.1: new high-speed USB device number 24 using ehci_hcd
[158146.572533] usb 2-1.1: device descriptor read/64, error -71
[158146.764498] usb 2-1.1: device descriptor read/64, error -71
[158146.940333] usb 2-1.1: new high-speed USB device number 25 using ehci_hcd
[158147.355705] usb 2-1.1: device not accepting address 25, error -71
[158147.427923] usb 2-1.1: new high-speed USB device number 26 using ehci_hcd
[158147.843222] usb 2-1.1: device not accepting address 26, error -71
[158147.843491] hub 2-1:1.0: unable to enumerate USB device on port 1

---

### Post by tfrue on 2014-04-29
With the drive connected, I would like to see the outputs of these commands:
```
lsusb
```
```
sudo blkid
```
```
lsblk
```
Thanks

---

