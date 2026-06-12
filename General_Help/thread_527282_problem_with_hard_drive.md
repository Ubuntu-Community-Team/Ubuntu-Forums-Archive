---
title: "problem with hard drive"
date: 2007-08-16
forum: General Help
---

### Post by EI-GrAd on 2007-08-16
```
[ 9313.328000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 9313.328000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 9313.328000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 9320.328000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 9343.344000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 9343.344000] ata1: soft resetting port
[ 9343.688000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 9343.696000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 9343.696000] ata1.00: configured for UDMA/100
[ 9343.884000] ata1.01: configured for UDMA/33
[ 9343.884000] ata1: EH complete
[ 9343.900000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 9343.908000] sda: Write Protect is off
[ 9343.908000] sda: Mode Sense: 00 3a 00 00
[ 9343.908000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9343.908000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 9344.364000] sda: Write Protect is off
[ 9344.364000] sda: Mode Sense: 00 3a 00 00
[ 9344.412000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

```
[10101.708000] sda: Mode Sense: 00 3a 00 00
[10101.712000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10152.224000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[10152.224000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[10152.224000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[10159.224000] ata1: port is slow to respond, please be patient (Status 0xd0)
[10182.240000] ata1: port failed to respond (30 secs, Status 0xd0)
[10182.240000] ata1: soft resetting port
[10182.584000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[10182.592000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[10182.592000] ata1.00: configured for UDMA/100
[10182.772000] ata1.01: configured for UDMA/33
[10182.772000] ata1: EH complete
[10182.788000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[10182.788000] sda: Write Protect is off
[10182.788000] sda: Mode Sense: 00 3a 00 00
[10182.800000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10182.800000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[10182.800000] sda: Write Protect is off
[10182.800000] sda: Mode Sense: 00 3a 00 00
[10182.804000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```
 %((( what to do??? all applications, that using hd, stops... sorry for my english...

---

### Post by dannyboy79 on 2007-08-16
after booting normally please show me the output of 
sudo fdisk -l
please show me the out of this
sudo hdparm -I /dev/sda
is this an external usb drive? is it possible that your bios is set to usb 2.0 only and the drive is actually usb 1.1 or usb 1.0? there's some bios's that have a settings called usb legacy support. try to turn that on. This is an error I haven't seen before. "port slow to respond"??? Not sure.

It doesn't sound good for ya though. read this:
[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/2c895e1ac0a8ccf9/d5e910d37451ca33](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/2c895e1ac0a8ccf9/d5e910d37451ca33)

it's most likely your drive, before giving up on it, take it and hook it to another computer running from a livecd so you can try to ddrescue all the stuff on it into an image to salvage anything important. OR, just try to mount it and see if you can read from it. It might be a problem with that specific drive and the controller on your motherboard.

Plus you're very vague on the scenario here. Did this all of a sudden occur? Have you had this drive long, is this your system disk? Has it been working for a long time? Are you using gutsy, feisty, edgy, dapper or which version? Which kernel? get this with uname -r.

---

### Post by EI-GrAd on 2007-08-16
> **"fdisk"]&#1044 said:**
> 
---
[quote="hdparm"]/dev/sda:

ATA device, with non-removable media
        Model Number:       HTS541080G9AT00                         
        Serial Number:      MP28XBXBH27GRS
        Firmware Revision:  MB4OA60A
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 3a 
        Supported: 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        LBA48  user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Vendor, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: 128 (0x80)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                Address Offset Reserved Area Boot
           *    SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
        58min for SECURITY ERASE UNIT. 
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct
> is this an external usb drive? no

> 
It doesn't sound good for ya though. read this:
[http://groups.google.com/group/fa.li...e910d37451ca33](http://groups.google.com/group/fa.li...e910d37451ca33) %( it is not about my problem

that is in acer travelmate2480 notebook... it's 1 year old...

ubuntu feisty... 2.6.20-16-generic...

---

### Post by dannyboy79 on 2007-08-16
> **EI-GrAd said:**
> ---

 no

 %( it is not about my problem

that is in acer travelmate2480 notebook... it's 1 year old...

ubuntu feisty... 2.6.20-16-generic...
Well I have to disagree, the link was clearly the same problem. It shows:
ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[10152.224000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[10152.224000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[10159.224000] ata1: port is slow to respond, please be patient (Status 0xd0)
[10182.240000] ata1: port failed to respond (30 secs, Status 0xd0)
[10182.240000] ata1: soft resetting port

is a real problem and I am unaware how to fix. maybe the link was cut off, here it is again [[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/2c895e1ac0a8ccf9/d5e910d37451ca33]](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/2c895e1ac0a8ccf9/d5e910d37451ca33])

If this all of a sudden is occuring then your drive is either dieing or dead. you can try to run from a livecd, then make sure your sda drive is NOT mounted anywhere, then run
sudo fsck /dev/sda
this will repair the filesystem but it doesn't appear to be a filesystem error, it's more like a hardware problem, meaning your drive is dieing.

---

### Post by hewe on 2007-09-29
I experience this as well. However after some searching on various forums I think this is a kernel problem since SATA is incorporated in the kernel. Many people experience similar problems resulting in "ata?: port is  slow to respond status(0xdb8). Does anybody know how to disable the check for sata during 
This fenomenen can also make  your boot very, very lengthy in case it will boot. In my case it sometimes boot and stops with an error message.

---

### Post by kiev on 2008-05-29
for me she showed up one time in the floor of hour, however as a result of this
problem I lost a mysql database - mysql innodb not start - "Accertion error" -
did not help even "innodb_force_recovery = 4", backup was an a week remoteness
- the works of whole department lost data for a few days, the management simply
in shock - I going to discharge from job (((

this problem already whole year:
-----------
I'm stumped trying to track down the below intermittent problem.....
I've confirmed this problem on 2.6.19, 2.6.20 and 2.6.21.
-----------
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765)
[http://kerneltrap.org/node/16175](http://kerneltrap.org/node/16175)

"System hang from time to time" [http://bugzilla.kernel.org/show_bug.cgi?id=8300](http://bugzilla.kernel.org/show_bug.cgi?id=8300)
"sata hotplug removal of drive freezes all 2.6.21 kernels"
[http://bugzilla.kernel.org/show_bug.cgi?id=8421](http://bugzilla.kernel.org/show_bug.cgi?id=8421)
"(sata_via) system freeze in random time"
[http://bugzilla.kernel.org/show_bug.cgi?id=9115](http://bugzilla.kernel.org/show_bug.cgi?id=9115)
"kernel freezes with on clockevent warning"
[http://bugzilla.kernel.org/show_bug.cgi?id=9834](http://bugzilla.kernel.org/show_bug.cgi?id=9834)
"[pata_ali] Unspecified hang on Acer laptop"
[http://bugzilla.kernel.org/show_bug.cgi?id=9898](http://bugzilla.kernel.org/show_bug.cgi?id=9898)
"System freezes after I/O on pata_jmicron device"
[http://bugzilla.kernel.org/show_bug.cgi?id=10296](http://bugzilla.kernel.org/show_bug.cgi?id=10296)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437)
[https://bugs.launchpad.net/ubuntu/+bug/226600](https://bugs.launchpad.net/ubuntu/+bug/226600)

"System hang from time to time" [http://bugzilla.kernel.org/show_bug.cgi?id=8300](http://bugzilla.kernel.org/show_bug.cgi?id=8300)

"sata hotplug removal of drive freezes all 2.6.21 kernels" [http://bugzilla.kernel.org/show_bug.cgi?id=8421](http://bugzilla.kernel.org/show_bug.cgi?id=8421)

"(sata_via) system freeze in random time" [http://bugzilla.kernel.org/show_bug.cgi?id=9115](http://bugzilla.kernel.org/show_bug.cgi?id=9115)

"System freezes after I/O on pata_jmicron device" [http://bugzilla.kernel.org/show_bug.cgi?id=10296](http://bugzilla.kernel.org/show_bug.cgi?id=10296) 

"weird message in syslog"  [http://ubuntuforums.org/showthread.php?t=760046](http://ubuntuforums.org/showthread.php?t=760046)




[B]
Development of linux reached an impasse.

Nobody can not do nothing![/B]

---

