---
title: "hdparm not working"
date: 2013-09-02
forum: General Help
---

### Post by Baswazz on 2013-09-02
Saturday i installed Ubuntu Server 12.04.03 LTS. The first thing i did is enable spindown by removing the # sign from the /etc/hdparm.conf spindown_time = 24
It did work perfect.
Yesterday morning i woke up and saw one of the disks was not in standby.

I tried edit /etc/hdparm.conf:
```
/dev/sdb {
spindown_time = 60
}
/dev/sdb {
spindown_time = 60
}
/dev/sdc {
spindown_time = 60
}
/dev/sdd {
spindown_time = 60
}
/dev/sde {
spindown_time = 60
}
/dev/sdf {
spindown_time = 60
}
/dev/sdg {
spindown_time = 60
}

```

No standby after 5 minutes after a reboot the disks are still active/idle. The APM setting is disabled (255). I also tried 127.

I added the spindown_time manually:
```
hdparm -S60 /dev/sd[b-g]
```

Nothing happen.

When i use -y it does work.
```
hdparm -y /dev/sd[b-g]
```

hdparm -I /dev/sdb:
```
/dev/sdb:

ATA device, with non-removable media
    Model Number:       Hitachi HDS5C4040ALE630                 
    Serial Number:      PL2321LAGAP0TJ
    Firmware Revision:  MPAOA3B0
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0; Revision: ATA8-AST T13 Project D1697 Revision 0b
Standards:
    Used: unknown (minor revision code 0x0029) 
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 7814037168
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:     3815447 MBytes
    device size with M = 1000*1000:     4000787 MBytes (4000 GB)
    cache/buffer size  = 25060 KBytes (type=DualPortCache)
    Form Factor: 3.5 inch
    Nominal Media Rotation Rate: 5700
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: disabled
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
            Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
            Advanced Power Management feature set
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
            Media Card Pass-Through
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    URG for READ_STREAM[_DMA]_EXT
       *    URG for WRITE_STREAM[_DMA]_EXT
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
            unknown 119[7]
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
            Non-Zero buffer offsets in DMA Setup FIS
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
            In-order data delivery
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
    not    supported: enhanced erase
    508min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000cca22ec4daa3
    NAA        : 5
    IEEE OUI    : 000cca
    Unique ID    : 22ec4daa3
Checksum: correct
```

Can anyone help me out thanks.

Only thing i did is:
update-rc.d -f hdparm remove

But when i add it again i get:
update-rc.d hdparm default
update-rc.d: /etc/init.d/hdparm: file does not exist

---

