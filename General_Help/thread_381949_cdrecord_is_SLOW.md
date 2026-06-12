---
title: "cdrecord is SLOW"
date: 2007-03-11
forum: General Help
---

### Post by rocketman768 on 2007-03-11
Hi all...cdrecord is extremely slow when used to burn cd's. I have a 48x burner (sony dru-120 D), and no matter what speed I tell cdrecord to burn at, it will always end up between 4x and 8x average. Also, I notice that the device buffer (which is 2MB) is frequently getting very close to 0 percent (every few seconds it goes low and gets filled back up).

I have made sure cdrecord is installed as SUID root and I also "sudo" it just to make sure. Could the problem be the "cannot gain SYS_RAWIO capability" as shown below?

```

Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.18.6
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.34
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c  

```

---

### Post by dcstar on 2007-03-11
> **rocketman768 said:**
> Hi all...cdrecord is extremely slow when used to burn cd's. I have a 48x burner (sony dru-120 D), and no matter what speed I tell cdrecord to burn at, it will always end up between 4x and 8x average. Also, I notice that the device buffer (which is 2MB) is frequently getting very close to 0 percent (every few seconds it goes low and gets filled back up).
.......

```
sudo hdparm -iI /dev/**xxxx**
``` where the** xxxx** is the device of your CD recorder, and check if you are using DMA.

---

### Post by rocketman768 on 2007-03-16
Here is the output from "sudo hdparm -iI /dev/hda" 

```

Model=SONY DVD RW DW-G120A, FwRev=MYR5, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode


ATAPI CD-ROM, with removable media
        Model Number:       SONY    DVD RW DW-G120A
        Serial Number:
        Firmware Revision:  MYR5
Standards:
        Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
        Supported: CD-ROM ATAPI-2
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: *sdma0 *sdma1 *sdma2 sdma3 sdma4 sdma7 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 (?)
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    PACKET command feature set
           *    DEVICE_RESET command
           *    Mandatory FLUSH_CACHE
HW reset results:
        CBLID- below Vih
        Device num = 0

```

---

