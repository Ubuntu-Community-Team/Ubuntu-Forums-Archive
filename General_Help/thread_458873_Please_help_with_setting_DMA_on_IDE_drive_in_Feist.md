---
title: "Please help with setting DMA on IDE drive in Feisty"
date: 2007-05-30
forum: General Help
---

### Post by SergeiFranco on 2007-05-30
Please help with setting DMA on IDE drive in Feisty, or whatever on to fix the slow drives (IDE PATA drives that is). The problem appeared since Feisty, as in Feisty all drives are SDX instead of HDX. hparm complaints about inappropriate ioctl. There is no fix anywhere. A lot of people having similar issiues:
[http://ubuntuforums.org/showthread.php?t=434177](http://ubuntuforums.org/showthread.php?t=434177)
[http://ubuntuforums.org/showthread.php?t=394404](http://ubuntuforums.org/showthread.php?t=394404)
[http://ubuntuforums.org/showthread.php?t=457732](http://ubuntuforums.org/showthread.php?t=457732)
[http://ubuntuforums.org/showthread.php?t=434443](http://ubuntuforums.org/showthread.php?t=434443)
[http://ubuntuforums.org/showthread.php?t=452165](http://ubuntuforums.org/showthread.php?t=452165)
[http://ubuntuforums.org/showthread.php?t=443327](http://ubuntuforums.org/showthread.php?t=443327)
[http://ubuntuforums.org/showthread.php?t=449238](http://ubuntuforums.org/showthread.php?t=449238)
[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)
[http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)
[http://ubuntuforums.org/showthread.php?t=253252](http://ubuntuforums.org/showthread.php?t=253252)
[http://ubuntuforums.org/showthread.php?t=434177](http://ubuntuforums.org/showthread.php?t=434177)
[http://ubuntuforums.org/showthread.php?t=128721](http://ubuntuforums.org/showthread.php?t=128721)
[http://ubuntuforums.org/showthread.php?t=427728](http://ubuntuforums.org/showthread.php?t=427728)
[http://ubuntuforums.org/showthread.php?t=422336](http://ubuntuforums.org/showthread.php?t=422336)
[http://ubuntuforums.org/showthread.php?t=420435](http://ubuntuforums.org/showthread.php?t=420435)
[http://ubuntuforums.org/showthread.php?t=410871](http://ubuntuforums.org/showthread.php?t=410871)
[http://ubuntuforums.org/showthread.php?t=324373](http://ubuntuforums.org/showthread.php?t=324373)
and so on...

Here is my problem:
```

sergei@sergei:~$ sudo hdparm -d1 /dev/sdd

/dev/sdd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

sergei@sergei:~$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   1718 MB in  2.00 seconds = 858.82 MB/sec
 Timing buffered disk reads:    8 MB in  3.41 seconds =   2.35 MB/sec

```

and here is the drive info:
```

sergei@sergei:~$ sudo hdparm /dev/sdd

/dev/sdd:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0

sergei@sergei:~$ sudo hdparm -iI /dev/sdd

/dev/sdd:

 Model=ST3250823A                              , FwRev=3.01    , SerialNo=            3ND00T1P
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode


ATA device, with non-removable media
        Model Number:       ST3250823A
        Serial Number:      3ND00T1P
        Firmware Revision:  3.01
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2
        Supported: 6 5 4
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  488397168
        device size with M = 1024*1024:      238475 MBytes
        device size with M = 1000*1000:      250059 MBytes (250 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = ?
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
                SET_MAX security extension
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART Command Transport (SCT) feature set
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by CSEL
Checksum: incorrect (0xe6), expected 0x1a


```

The HDD controller is a ITE RAID PATA PCI 8212.
The 2Mb/s part is the most annoying - I can download faster :(

Help!

---

### Post by hardyn on 2007-05-30
the fiesty ..20.15 kernel assumes that all drives are SATA, where DMA is assumed.

this is repaired in ...20.16 kernel, the new updated one; BUT! there is some trouble with it, you will be able to do what you have tired with the new kenel, IF the kernel works for you.

check out the ...20.16 kernel theads to see if looks like the kernel update will work for you... as allways, kernel updates are sensitive, be careful!

good luck.

---

### Post by SergeiFranco on 2007-05-30
```
sergei@sergei:~$ uname -a
Linux sergei 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

```

Problem is still there.

---

### Post by hardyn on 2007-05-30
Hmmm thats intersting... its worked fine for me.

launchpad?

---

### Post by chalewa on 2007-05-30
problem still exists for me as well...even with the updated kernel

---

### Post by SergeiFranco on 2007-05-31
Has any one else got the same problem? If so we must submit bug but I never done it before....

---

### Post by SergeiFranco on 2007-06-21
This is ridiculous, there has been 2 or 3 kernel updates and THE PROBLEM IS NOT FIXED!
I get the feeling that I am not the only one, there are hundreds or even thousands of people with that problem.
Most of them have problem with DVD drives, many of them went back to Windows or other distro.

It is a show stopper.
Of course no one cares.... 
Instead of advertising "free extensive support via forum", you should put "you are on your own pal".
I have asked a lot of questions and none of them were answered.

A lot of small annoyances drive me insane...
So I am sorry if I offended anyone.

But there has to be something done (and no, launchpad looks worse than this forum - it is just overflowed with bug reports) in terms of organizing the solutions into one SOLVED sub-forum. And current bugs into other sub-forum. Solved posts should be edited and merged into 1 thread with irrelevant and not current info removed.
It is really frustrating to find hundreds completely different HOW-TO install Beryl guides.
I can write 100 pages on what could be improved in Ubuntu and ubuntuforums but I doubt anyone cares....

---

### Post by rjtd on 2007-07-01
Same problem here with 2.6.20-16 as well.
Hard disc drive is running without DMA and using 16 bit mode, and my PC crawls to dead every time it is accessing HDD.
FIX THIS PLEASE!

---

### Post by ihristov on 2007-07-02
Me too. Have an older system where the DVD would not work because it was being set in UDMA 4 mode. It reports that supports it, but in actuallity it only supports UDMA 2 at best.

As discussed all over the place now hdparm does not work and sdparm does not support (nor will ever) the IDE specific parameters that hdparam supports.

As a temporary fix I have manually installed the older 2.6.17 (Edgy) kernel and all is back to normal.
BTW: With the 2.6.17 kernel (when the DVD drive is seen as /dev/hdc instead of /dev/scd0) the device is set in UDMA 2 mode automatically. Not sure why, but it is.

The big caveat with this solution is that:

1) Need to be careful not to install a new kernel

2) You can't afford to manually install a kernel and expect that all will be fine if you are using additional restricted drivers (like NVidia). I fall under this category on my laptop where I use the binary NVidia and the VMWare driver.

After you have read all of the above: Use at your own risk

How to install.

1) Download the latest available Edgy kernel from  [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/)  (or copy it from /var/cache/apt/archives/ from an Edgy installation)

It appears the last available is [linux-image-2.6.17-50-generic_2.6.17.1-50.50_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-50-generic_2.6.17.1-50.50_i386.deb")

2) install it either via the GUI (with GDebi) or with "dpkg -i"

3) check to make sure there is an entry for it in /boot/grub/menu.lst
If there is no added entry add it by hand

4) reboot and test

---

