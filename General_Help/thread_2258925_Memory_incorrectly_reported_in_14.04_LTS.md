---
title: "Memory incorrectly reported in 14.04 LTS"
date: 2014-12-31
forum: General Help
---

### Post by parthamage on 2014-12-31
Yesterday I installed 14.04 LTS in my new HTPC rig - details below.  Bottom line is that on first boot, although I am running 64 bit, and I have 8 gigs of RAM installed that the BIOS sees, at first, Ubuntu said I had 3.2 gigs.  I went into the BIOS to check on a few things.  Decided instead of "Auto" memory sharing, I want to allocate 2 gigs of my 8 to shared video, primarily for video and gaming.  Boot back into Ubuntu, and is now reporting I only have 1.2 gigs of memory!  System details follow:

CPU:  AMD A10-7850K 3.7GHz Quad-Core
CPU Cooler:  Cooler Master Seidon 120M 86.2 CFM Liquid
Motherboard:  ASRock FM2A88X-ITX+ Mini ITX FM2+
Memory:  G.Skill Ripjaws Z Series 8GB (2 x 4GB) DDR3-2400
Storage:  Crucial MX100 256GB 2.5" SSD, Western Digital Caviar Blue 1TB 3.5" 7200RPM
Case:  Cooler Master Elite 130 Mini ITX Tower
Power Supply:  Corsair 430W ATX12V
Optical Drive:  LG WH16NS40 Blu-Ray/DVD/CD Writer

Thanks, all!  Happy New Year!
Charles

---

### Post by slickymaster on 2014-12-31
See these threads:
[Ubuntu 14.04 64 bit only detects 4 out of 8 GB of RAM]("http://ubuntuforums.org/showthread.php?t=2247626")
[Ubuntu seeing only half of my ram]("http://ubuntuforums.org/showthread.php?t=2168355")

---

### Post by parthamage on 2014-12-31
Free -m doesn't see the memory - it looks like I'm almost maxed out.  However, dmidecode sees all of it - both sticks.  See below:

```
perry@perry-htpc:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1795       1692        102         42         16        356
-/+ buffers/cache:       1319        476
Swap:         8383          1       8382
```


```
perry@perry-htpc:~$ sudo dmidecode
# dmidecode 2.12
SMBIOS 2.7 present.
17 structures occupying 1057 bytes.
Table at 0x000EBF50.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: P2.40
    Release Date: 08/01/2014
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 8192 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: To Be Filled By O.E.M.
    Product Name: To Be Filled By O.E.M.
    Version: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    UUID: 03000200-0400-0500-0006-000700080009
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASRock
    Product Name: FM2A88X-ITX+
    Version:                       
    Serial Number: E80-48027200380
    Asset Tag:                       
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis:                       
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
    Manufacturer: To Be Filled By O.E.M.
    Type: Desktop
    Lock: Not Present
    Version: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0
    SKU Number: To be filled by O.E.M.

Handle 0x0004, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE1
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 17
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:15.0

Handle 0x0005, DMI type 11, 5 bytes
OEM Strings
    String 1: To Be Filled By O.E.M.

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 CACHE
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: 1 ns
    Error Correction Type: Multi-bit ECC
    System Type: Unified
    Associativity: 2-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 CACHE
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 4096 kB
    Maximum Size: 4096 kB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: 1 ns
    Error Correction Type: Multi-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x000C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x000E, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x000F, DMI type 19, 31 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Physical Array Handle: 0x000E
    Partition Width: 255

Handle 0x0010, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM 0
    Bank Locator: CHANNEL A
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 2400 MHz
    Manufacturer: <BAD INDEX>
    Serial Number: 00000000
    Asset Tag: A1_AssetTagNum0
    Part Number: F3-19200CL9-4GBZMD
    Rank: 2
    Configured Clock Speed: 2400 MHz

Handle 0x0011, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Physical Device Handle: 0x0010
    Memory Array Mapped Address Handle: 0x000F
    Partition Row Position: 1

Handle 0x0012, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM 0
    Bank Locator: CHANNEL B
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 2400 MHz
    Manufacturer: <BAD INDEX>
    Serial Number: 00000000
    Asset Tag: A1_AssetTagNum1
    Part Number: F3-2400C10-4GZH
    Rank: 2
    Configured Clock Speed: 2400 MHz

Handle 0x0013, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00100000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 4 GB
    Physical Device Handle: 0x0012
    Memory Array Mapped Address Handle: 0x000F
    Partition Row Position: 1

Handle 0x0016, DMI type 4, 42 bytes
Processor Information
    Socket Designation: CPUSocket
    Type: Central Processor
    Family: A-Series
    Manufacturer: AMD
    ID: 01 0F 63 00 FF FB 8B 17
    Signature: Family 21, Model 48, Stepping 1
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        HTT (Multi-threading)
    Version: AMD A10-7850K Radeon R7, 12 Compute Cores 4C+8G
    Voltage: 1.3 V
    External Clock: 100 MHz
    Max Speed: 3700 MHz
    Current Speed: 3700 MHz
    Status: Populated, Enabled
    Upgrade: Socket FM2
    L1 Cache Handle: 0x0006
    L2 Cache Handle: 0x0007
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 4
    Characteristics:
        64-bit capable

Handle 0x0017, DMI type 127, 4 bytes
End Of Table
```

Thanks!

---

