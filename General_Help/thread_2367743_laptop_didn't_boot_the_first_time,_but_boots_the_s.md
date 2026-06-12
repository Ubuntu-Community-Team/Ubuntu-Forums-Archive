---
title: "laptop didn't boot the first time, but boots the second"
date: 2017-08-02
forum: General Help
---

### Post by ardouronerous on 2017-08-02
The laptop is a Dell Inspiron E1505 running Lubuntu 16.04, with 120GB SSD and 1GB RAM (two 512MB RAM), this laptop was bought in 2007.

The laptop usually takes 2 to 3 seconds to boot due to the SSD installed, but this morning, the laptop didn't boot, the Dell logo comes but doesn't boot into Lubuntu, but after pressing the power button to turn off the laptop and waiting for a few seconds, turns laptop back on and it boots all the way, even tested it by restarting, it boots.

I read somewhere this could be faulty RAM, how do I determine this on Lubuntu?

---

### Post by BenginM on 2017-08-03
in GRUB menu , Do a MemTest86 ..

how old or new is this lubuntu installation , Do you have a swap partition or a swapfile ?

$ swapon -s

 Dose the laptop have the most current BIOS

$ inxi -M

 and the most current firmware for the SSD.

```
 sudo hdparm -I /dev/x 

sudo hdparm -I /dev/sda | grep Firmware
```

where x is the SSD device drive , usually it's sda 
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

you should see something like :

```


sary@blu:~$ inxi -M
Machine:   System: Hewlett-Packard product: 120-1034
           Mobo: Quanta model: 2AC7 v: 011 Bios: AMI v: ARM_702 date: 07/26/2011
sary@blu:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       Hitachi HDS721010CLA632                 
    Serial Number:      JP2940J828DZHV
    Firmware Revision:  JP4OA41A
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
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
    LBA48  user addressable sectors: 1953525168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      953869 MBytes
    device size with M = 1000*1000:     1000204 MBytes (1000 GB)
    cache/buffer size  = 29999 KBytes (type=DualPortCache)
    Form Factor: 3.5 inch
    Nominal Media Rotation Rate: 7200
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 0
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Write Same (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    232min for SECURITY ERASE UNIT. 234min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000cca396e002b7
    NAA        : 5
    IEEE OUI    : 000cca
    Unique ID    : 396e002b7


```

also , check the S.M.A.R.T status of the ssd ,a good resource on this , using:

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

you can write the result to a file:

```
sudo smartctl -a /dev/sda > smart-results.txt
```
 Also you may want to disable unused/unwanted kernel modules ,and services from loading ..

after all GNU/linux is considered heavy these days , and this is 2017 , consider adding more RAM!

---

### Post by ardouronerous on 2017-08-03
> **BenginM said:**
> in GRUB menu , Do a MemTest86 ..

Not sure how to get to the GRUB menu though, anyway to do a memtest from within Lubuntu's terminal?

> how old or new is this lubuntu installation , Do you have a swap partition or a swapfile ?

$ swapon -s

I think it's about a month and a half old installation, because I bought the SSD a month and a half ago.
```
swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                                  partition    1036284    225400    -1
```

> Dose the laptop have the most current BIOS

$ inxi -M

```
inxi -M
Machine:   System: Dell (portable) product: MM061
           Mobo: Dell model: 0KD882 Bios: Dell v: A08 date: 07/28/2006
```

 > and the most current firmware for the SSD.

```
 sudo hdparm -I /dev/x 

sudo hdparm -I /dev/sda | grep Firmware
```

where x is the SSD device drive , usually it's sda 

you should see something like :

```


sary@blu:~$ inxi -M
Machine:   System: Hewlett-Packard product: 120-1034
           Mobo: Quanta model: 2AC7 v: 011 Bios: AMI v: ARM_702 date: 07/26/2011
sary@blu:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       Hitachi HDS721010CLA632                 
    Serial Number:      JP2940J828DZHV
    Firmware Revision:  JP4OA41A
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
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
    LBA48  user addressable sectors: 1953525168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      953869 MBytes
    device size with M = 1000*1000:     1000204 MBytes (1000 GB)
    cache/buffer size  = 29999 KBytes (type=DualPortCache)
    Form Factor: 3.5 inch
    Nominal Media Rotation Rate: 7200
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 0
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Write Same (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    232min for SECURITY ERASE UNIT. 234min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000cca396e002b7
    NAA        : 5
    IEEE OUI    : 000cca
    Unique ID    : 396e002b7


```

also , check the S.M.A.R.T status of the ssd ,a good resource on this , using:

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

you can write the result to a file:

```
sudo smartctl -a /dev/sda > smart-results.txt
```
 Also you may want to disable unused/unwanted kernel modules ,and services from loading ..

```
sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       WDC WDS120G1G0A-00SS50                  
    Serial Number:      171301A00E4C        
    Firmware Revision:  Z3311000
    Media Serial Num:   
    Media Manufacturer: 
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Used: unknown (minor revision code 0x0110) 
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  234441648
    LBA48  user addressable sectors:  234441648
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:      114473 MBytes
    device size with M = 1000*1000:      120034 MBytes (120 GB)
    cache/buffer size  = unknown
    Form Factor: 2.5 inch
    Nominal Media Rotation Rate: Solid State Device
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 1    Current = 1
    Advanced power management level: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
       *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
            DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
            Device Sleep (DEVSLP)
       *    DOWNLOAD MICROCODE DMA command
       *    WRITE BUFFER DMA command
       *    READ BUFFER DMA command
       *    Data Set Management TRIM supported (limit 8 blocks)
       *    Deterministic read ZEROs after TRIM
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5001b448b4ee0216
    NAA        : 5
    IEEE OUI    : 001b44
    Unique ID    : 8b4ee0216
Device Sleep:
    DEVSLP Exit Timeout (DETO): 90 ms (drive)
    Minimum DEVSLP Assertion Time (MDAT): 26 ms (drive)
Checksum: correct

```

```
smartctl 6.5 2016-01-24 r4214 [i686-linux-4.10.0-28-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WDS120G1G0A-00SS50
Serial Number:    171301A00E4C
LU WWN Device Id: 5 001b44 8b4ee0216
Firmware Version: Z3311000
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Thu Aug  3 13:24:50 2017 PHT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x11) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  10) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   000   100   000    Old_age   Always       -       280
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       56
165 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       4297261086
166 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
167 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
168 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1
169 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
170 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
171 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       2
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   054   046   000    Old_age   Always       -       46 (Min/Max 0/54)
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       0
230 Unknown_SSD_Attribute   0x0032   100   100   000    Old_age   Always       -       42949935114
232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       100
233 Media_Wearout_Indicator 0x0032   100   100   000    Old_age   Always       -       37
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       141
241 Total_LBAs_Written      0x0030   253   253   000    Old_age   Offline      -       112
242 Total_LBAs_Read         0x0030   253   253   000    Old_age   Offline      -       141
244 Unknown_Attribute       0x0032   000   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Selective Self-tests/Logging not supported


```

> after all GNU/linux is considered heavy these days , and this is 2017 , consider adding more RAM!

Unforunately, finding DD2 RAM for laptops is kinda difficult, because I don't have a credit card or even a debit card, so online shopping isn't available to me.

---

### Post by BenginM on 2017-08-03
> **ardouronerous said:**
> Not sure how to get to the GRUB menu though, anyway to do a memtest from within Lubuntu's terminal? 

no that's not how it works , if this is an EFI BIOS installation hit the ESC key after the BIOS screen , right shift if it's a legacy BIOS installation

I think it's about a month and a half old installation, because I bought the SSD a month and a half ago.

```
swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                                  partition    1036284    225400    -1
```

the swap ratio looks ok ..

```
inxi -M
Machine:   System: Dell (portable) product: MM061
           Mobo: Dell model: 0KD882 Bios: Dell v: A08 date: 07/28/2006
```

 
there seems to be a BIOS update for Dell Inspiron 6400/E1505 BIOS, A17

and i couldn't find a firmware update for the SSD  the SSD seems to be this

[http://ssd.userbenchmark.com/SpeedTest/201586/WDC-WDS120G1G0A-00SS50](http://ssd.userbenchmark.com/SpeedTest/201586/WDC-WDS120G1G0A-00SS50)

>  Unfortunately, finding DD2 RAM for laptops is kinda difficult, because I don't have a credit card or even a debit card, so online shopping isn't available to me.

Chea! that's understandable , The system will support this - 512MB/1GB/2GB 533MHz/667MHz DDR2 SDRAM Memory.

[https://wiki.archlinux.org/index.php/Dell_Inspiron_6400#Base_Components](https://wiki.archlinux.org/index.php/Dell_Inspiron_6400#Base_Components)

---

### Post by ardouronerous on 2017-08-03
> **BenginM said:**
> no that's not how it works , if this is an EFI BIOS installation hit the ESC key after the BIOS screen , right shift if it's a legacy BIOS installation

I think it's about a month and a half old installation, because I bought the SSD a month and a half ago.

```
swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                                  partition    1036284    225400    -1
```

the swap ratio looks ok ..

After Googling on how to run memtest on the terminal, I found and installed memtester, here's the results;
```
~$ sudo memtester 1024 5 
memtester version 4.3.0 (32-bit)
Copyright (C) 2001-2012 Charles Cazabon.
Licensed under the GNU General Public License version 2 (only).

pagesize is 4096
pagesizemask is 0xfffff000
want 1024MB (1073741824 bytes)
got  818MB (858349568 bytes), trying mlock ...locked.
Loop 1/5:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : ok         
  Bit Spread          : ok         
  Bit Flip            : ok         
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Loop 2/5:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : ok         
  Bit Spread          : ok         
  Bit Flip            : ok         
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Loop 3/5:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : ok         
  Bit Spread          : ok         
  Bit Flip            : ok         
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Loop 4/5:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : ok         
  Bit Spread          : ok         
  Bit Flip            : ok         
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Loop 5/5:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : ok         
  Bit Spread          : ok         
  Bit Flip            : ok         
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Done.
```

> ```
inxi -M
Machine:   System: Dell (portable) product: MM061
           Mobo: Dell model: 0KD882 Bios: Dell v: A08 date: 07/28/2006
```

 
there seems to be a BIOS update for Dell Inspiron 6400/E1505 BIOS, A17

and i couldn't find a firmware update for the SSD , am not sure where to look as only you know the exact laptop model , the SSD seems to be this

[http://ssd.userbenchmark.com/SpeedTest/201586/WDC-WDS120G1G0A-00SS50](http://ssd.userbenchmark.com/SpeedTest/201586/WDC-WDS120G1G0A-00SS50)



Chea! that's understandable , The system will support this - 512MB/1GB/2GB 533MHz/667MHz DDR2 SDRAM Memory.

[https://wiki.archlinux.org/index.php/Dell_Inspiron_6400#Base_Components](https://wiki.archlinux.org/index.php/Dell_Inspiron_6400#Base_Components)

On updating the BIOS, I have zero experience in flashing BIOS and I'm kinda hesitant of doing that because I heard so many horror stories of people bricking their PCs when updating their BIOS.

---

### Post by BenginM on 2017-08-03
Well ok, now i can only think of two things ,the swap partition on sda5** UUID** entry in /etc/fstab matches the output of sudo blkid! , in my system it does:

```


sary@blu:~$ sudo blkid
[sudo] password for sary: 
/dev/sda1: UUID="faf0b5bd-d445-4294-8474-d0e9d286a528" TYPE="ext4" PARTUUID="66e5bf29-01"
/dev/sda2: UUID="688e1192-75a7-4391-8230-276ec3f746e5" TYPE="swap" PARTUUID="66e5bf29-02"
/dev/sda3: UUID="cd891609-3d04-42e2-999d-962a36991922" TYPE="ext4" PARTUUID="66e5bf29-03"
/dev/sdb1: LABEL="MYPASSPORT" UUID="544A-44A6" TYPE="vfat" PARTUUID="44fdfe06-01"
sary@blu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=faf0b5bd-d445-4294-8474-d0e9d286a528 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=688e1192-75a7-4391-8230-276ec3f746e5 none            swap    sw              0       0


```

Two, is to preform a filesystem check on the ssd ..

from recovery (safe) mode drop to a root shell , and type:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

mount -o remount,rw /
fsck -f
mount -o remount,ro /
sync
reboot

---

### Post by ardouronerous on 2017-08-03
> **BenginM said:**
> Well ok, now i can only think of two things ,the swap partition on sda5** UUID** entry in /etc/fstab matches the output of sudo blkid! , in my system it does:

```


sary@blu:~$ sudo blkid
[sudo] password for sary: 
/dev/sda1: UUID="faf0b5bd-d445-4294-8474-d0e9d286a528" TYPE="ext4" PARTUUID="66e5bf29-01"
/dev/sda2: UUID="688e1192-75a7-4391-8230-276ec3f746e5" TYPE="swap" PARTUUID="66e5bf29-02"
/dev/sda3: UUID="cd891609-3d04-42e2-999d-962a36991922" TYPE="ext4" PARTUUID="66e5bf29-03"
/dev/sdb1: LABEL="MYPASSPORT" UUID="544A-44A6" TYPE="vfat" PARTUUID="44fdfe06-01"
sary@blu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=faf0b5bd-d445-4294-8474-d0e9d286a528 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=688e1192-75a7-4391-8230-276ec3f746e5 none            swap    sw              0       0


```

```
sudo blkid
/dev/sda1: UUID="14768fcd-773e-466a-97a2-db6837c043e5" TYPE="ext4" PARTUUID="b973a9b3-01"
/dev/sda5: UUID="c6d3b4b8-976d-4d82-981b-7f0afc2a4bd2" TYPE="swap" PARTUUID="b973a9b3-05"
```


> Two, is to preform a filesystem check on the ssd ..

from recovery (safe) mode drop to a root shell , and type:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

mount -o remount,rw /
fsck -f
mount -o remount,ro /
sync
reboot

This failed though, as it told me the drive was still mounted.

Anyway to do a filesystem check on the terminal?

Anyway, I'm not experiencing any booting issues this morning.

---

