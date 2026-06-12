---
title: "Laptop beeps and shut down instantly"
date: 2021-07-01
forum: General Help
---

### Post by monkeybrain20122 on 2021-07-01
Hi, this was unnerving and out of the blue. My laptop has been working in top shape but today all of a sudden it went black with several beeping sound like a siren. When I reboot again it makes that beep sound again but I do manage to boot to the desktop, but instantly it will go black and shut down. The machine's temperature was about 50C at the time, well below the threshold and I wasn't doing anything cpu or GPU intensive, I was just editing a text file with gedit.

I tried to boot into recovery mode but it shut down after a minute or so as well and all the options didn't work saying some files didn't exist. When I booted back to the desktop, I tried to run a few commands on the terminal and realized on reboot that they were not recorded in bash history. 

I tried to boot from a Ubuntu live usb but the same happened, it started beeping and the live usb shut down as well.

Then I noticed that the beep sound kind of went away if I unplugged the power and used just the battery. I said "kind of" because it still beeped sometimes on reboot but not every time. But still the machine shut down a minute or so after booting into the desktop. I tried to boot from the usb without success many times then suddenly it worked. Once in the usb I did a lot of hardware tests. I tested the motherboard with dmidecode, I tested the hard drive with nvme-cli, I test the cpu with s-tui  the ram with memtester and all seems ok, I spent a few hours in the live session without the machine shutting down. When I booted into my hard drive again and this time everything works normally. I then ran another test for the gpu, again everything was fine. 

The full report
```
sudo dmidecode
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.
Table at 0x3FA15000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1.05.02dRSA2-1
    Release Date: 02/20/2017
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 16 MB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Print screen service is supported (int 5h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 5.12

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer:  System76
    Product Name:  Oryx Pro
    Version:  oryp3-ess
    Serial Number: Not Applicable         
    UUID: 4a5bfa80-fbfa-0000-0000-000000000000
    Wake-up Type: Power Switch
    SKU Number: Not Applicable                  
    Family: Not Applicable                  

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer:  System76
    Product Name:  Oryx Pro
    Version:  oryp3-ess
    Serial Number: Not Applicable        
    Asset Tag: Tag 12345
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
    Manufacturer:  System76
    Type: Notebook
    Lock: Not Present
    Version: N/A                             
    Serial Number: None                  
    Asset Tag: No Asset Tag
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0
    SKU Number: To Be Filled By O.E.M.

Handle 0x0004, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AJ_SPDIF1
    Internal Connector Type: None
    External Reference Designator: AUDIO
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0005, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AJ_MIC1
    Internal Connector Type: None
    External Reference Designator: AUDIO
    External Connector Type: Other
    Port Type: Audio Port

Handle 0x0006, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AJ_SIDE1
    Internal Connector Type: None
    External Reference Designator: AUDIO
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: KJ_SIM1
    Internal Connector Type: None
    External Reference Designator: SIM
    External Connector Type: Other
    Port Type: Other

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: KJ_CARD1
    Internal Connector Type: None
    External Reference Designator: CardRD
    External Connector Type: Other
    Port Type: Cardbus

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J_MDP1
    Internal Connector Type: None
    External Reference Designator: DP1
    External Connector Type: Other
    Port Type: Video Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J_MDP2
    Internal Connector Type: None
    External Reference Designator: DP2
    External Connector Type: Other
    Port Type: Video Port

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J_HDMI1
    Internal Connector Type: None
    External Reference Designator: HDMI
    External Connector Type: Other
    Port Type: Video Port

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J_USB3_1
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J_USB3_2
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ZJ_USB3_1
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ZJ_RJ1
    Internal Connector Type: None
    External Reference Designator: LAN
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J_TYPEC1
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: H_TYPEC2
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0012, DMI type 9, 17 bytes
System Slot Information
    Designation: U39A
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:01.0

Handle 0x0013, DMI type 9, 17 bytes
System Slot Information
    Designation: U55A
    Type: x4 PCI Express x4
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.0

Handle 0x0014, DMI type 9, 17 bytes
System Slot Information
    Designation: KU3
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.4

Handle 0x0015, DMI type 9, 17 bytes
System Slot Information
    Designation: J_SSD1
    Type: x4 PCI Express x4
    Current Usage: In Use
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1d.0

Handle 0x0016, DMI type 9, 17 bytes
System Slot Information
    Designation: J_WLAN1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.6

Handle 0x0017, DMI type 9, 17 bytes
System Slot Information
    Designation: J_WLAN1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 5
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.7

Handle 0x0018, DMI type 9, 17 bytes
System Slot Information
    Designation: J_SSD2
    Type: x4 PCI Express x4
    Current Usage: In Use
    Length: Short
    ID: 6
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1e.1

Handle 0x0019, DMI type 10, 10 bytes
On Board Device 1 Information
    Type: Video
    Status: Enabled
    Description:    DGPU
On Board Device 2 Information
    Type: Ethernet
    Status: Enabled
    Description: GLan
On Board Device 3 Information
    Type: Sound
    Status: Enabled
    Description:    HD-Audio

Handle 0x001A, DMI type 11, 5 bytes
OEM Strings
    String 1: 1558
    String 2: OEM String
    String 3: To Be Filled By O.E.M.
    String 4: To Be Filled By O.E.M.
    String 5: BIOS:1.05.02dRSA1

Handle 0x001B, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x001C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x001D, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 64 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001E, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 16384 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2400 MT/s
    Manufacturer: 8945
    Serial Number: 01010101
    Asset Tag: 9876543210
    Part Number: GKE160SO102408-2400 
    Rank: 2
    Configured Memory Speed: 2400 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V

Handle 0x001F, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: ChannelA-DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Memory Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown

Handle 0x0020, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 16384 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2400 MT/s
    Manufacturer: 8945
    Serial Number: 01010101
    Asset Tag: 9876543210
    Part Number: GKE160SO102408-2400 
    Rank: 2
    Configured Memory Speed: 2400 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V

Handle 0x0021, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: ChannelB-DIMM1
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Memory Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown

Handle 0x0022, DMI type 19, 31 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x007FFFFFFFF
    Range Size: 32 GB
    Physical Array Handle: 0x001D
    Partition Width: 2

Handle 0x0023, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0024, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 1024 kB
    Maximum Size: 1024 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0025, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3 Cache
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 8192 kB
    Maximum Size: 8192 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Multi-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x0026, DMI type 4, 48 bytes
Processor Information
    Socket Designation: U3E1
    Type: Central Processor
    Family: Core i7
    Manufacturer: Intel(R) Corporation
    ID: E9 06 09 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 158, Stepping 9
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
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM) i7-7820HK CPU @ 2.90GHz
    Voltage: 0.9 V
    External Clock: 100 MHz
    Max Speed: 8300 MHz
    Current Speed: 2800 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0023
    L2 Cache Handle: 0x0024
    L3 Cache Handle: 0x0025
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable
        Multi-Core
        Hardware Thread
        Execute Protection
        Enhanced Virtualization
        Power/Performance Control

Handle 0x0027, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x003FFFFFFFF
    Range Size: 16 GB
    Physical Device Handle: 0x001E
    Memory Array Mapped Address Handle: 0x0022
    Partition Row Position: Unknown
    Interleave Position: 1
    Interleaved Data Depth: 2

Handle 0x0028, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00400000000
    Ending Address: 0x007FFFFFFFF
    Range Size: 16 GB
    Physical Device Handle: 0x0020
    Memory Array Mapped Address Handle: 0x0022
    Partition Row Position: Unknown
    Interleave Position: 2
    Interleaved Data Depth: 2

Handle 0x0029, DMI type 130, 20 bytes
OEM-specific Type
    Header and Data:
        82 14 29 00 24 41 4D 54 00 00 00 00 00 A5 AF 02
        C0 00 00 00

Handle 0x002A, DMI type 131, 64 bytes
OEM-specific Type
    Header and Data:
        83 40 2A 00 31 00 00 00 00 00 00 00 00 00 00 00
        F8 00 52 A1 00 00 00 00 01 00 00 00 08 00 0B 00
        2A 0E 46 00 00 00 00 00 FE 00 FF FF 00 00 00 00
        00 00 00 00 22 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x002B, DMI type 221, 26 bytes
OEM-specific Type
    Header and Data:
        DD 1A 2B 00 03 01 00 01 02 00 00 00 02 00 00 00
        00 48 00 03 00 00 05 00 00 00
    Strings:
        Reference Code - CPU
        uCode Version
        TXT ACM version

Handle 0x002C, DMI type 221, 26 bytes
OEM-specific Type
    Header and Data:
        DD 1A 2C 00 03 01 00 01 02 00 00 00 02 00 00 00
        00 00 00 03 04 0B 08 46 2A 0E
    Strings:
        Reference Code - ME 11.0
        MEBx version
        ME Firmware Version
        Consumer SKU

Handle 0x002D, DMI type 221, 75 bytes
OEM-specific Type
    Header and Data:
        DD 4B 2D 00 0A 01 00 01 02 00 00 00 02 03 FF FF
        FF FF FF 04 00 FF FF FF 31 00 05 00 FF FF FF 31
        00 06 00 FF FF FF FF FF 07 00 3E 00 00 00 00 08
        00 34 00 00 00 00 09 00 0B 00 00 00 00 0A 00 3E
        00 00 00 00 0B 00 34 00 00 00 00
    Strings:
        Reference Code - SKL PCH
        PCH-CRID Status
        Disabled
        PCH-CRID Original Value
        PCH-CRID New Value
        OPROM - RST - RAID
        SKL PCH H Bx Hsio Version
        SKL PCH H Dx Hsio Version
        KBL PCH H Ax Hsio Version
        SKL PCH LP Bx Hsio Version
        SKL PCH LP Cx Hsio Version

Handle 0x002E, DMI type 221, 54 bytes
OEM-specific Type
    Header and Data:
        DD 36 2E 00 07 01 00 01 02 00 00 00 02 00 01 02
        00 00 00 03 00 01 02 00 00 00 04 05 FF FF FF FF
        FF 06 00 FF FF FF 05 00 07 00 FF FF FF 05 00 08
        00 FF FF FF FF FF
    Strings:
        Reference Code - SA - System Agent
        Reference Code - MRC
        SA - PCIe Version
        SA-CRID Status
        Disabled
        SA-CRID Original Value
        SA-CRID New Value
        OPROM - VBIOS

Handle 0x002F, DMI type 221, 103 bytes
OEM-specific Type
    Header and Data:
        DD 67 2F 00 0E 01 00 00 00 00 00 00 02 00 FF FF
        FF FF FF 03 04 FF FF FF FF FF 05 06 FF FF FF FF
        FF 07 08 FF FF FF FF FF 09 00 00 00 00 00 00 0A
        00 FF FF FF FF 00 0B 00 FF FF 00 00 00 0C 00 FF
        FF FF FF FF 0D 00 FF FF FF FF FF 0E 00 FF FF FF
        FF FF 0F 00 FF FF FF FF FF 10 11 01 03 03 01 00
        12 00 00 07 03 00 00
    Strings:
        Lan Phy Version
        Sensor Firmware Version
        Debug Mode Status
        Disabled
        Performance Mode Status
        Disabled
        Debug Use USB(Disabled:Serial)
        Disabled
        ICC Overclocking Version
        UNDI Version
        EC FW Version
        GOP Version
        BIOS Guard Version
        Base EC FW Version
        EC-EC Protocol Version
        Royal Park Version
        BP1.3.3.0_RP01
        Platform Version

Handle 0x0030, DMI type 136, 6 bytes
OEM-specific Type
    Header and Data:
        88 06 30 00 00 00

Handle 0x0031, DMI type 14, 20 bytes
Group Associations
    Name: Firmware Version Info
    Items: 5
        0x002B (OEM-specific)
        0x002C (OEM-specific)
        0x002D (OEM-specific)
        0x002E (OEM-specific)
        0x002F (OEM-specific)

Handle 0x0032, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0033, DMI type 14, 8 bytes
Group Associations
    Name: $MEI
    Items: 1
        0x0000 (OEM-specific)

Handle 0x0034, DMI type 219, 81 bytes
OEM-specific Type
    Header and Data:
        DB 51 34 00 01 03 01 45 02 00 A0 06 03 10 80 20
        00 00 00 00 40 08 00 00 00 00 00 00 00 00 40 02
        FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF
        FF FF FF FF FF FF FF FF 03 00 00 00 80 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00
    Strings:
        MEI1
        MEI2
        MEI3

Handle 0x0035, DMI type 127, 4 bytes
End Of Table

####################################
$ sudo dmidecode | grep -B 2 Stat
    Serial Number: None                  
    Asset Tag: No Asset Tag
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
--
On Board Device 1 Information
    Type: Video
    Status: Enabled
--
On Board Device 2 Information
    Type: Ethernet
    Status: Enabled
--
On Board Device 3 Information
    Type: Sound
    Status: Enabled
--
Handle 0x001C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected
--
    Max Speed: 8300 MHz
    Current Speed: 2800 MHz
    Status: Populated, Enabled
--
    Strings:
        Reference Code - SKL PCH
        PCH-CRID Status
--
        Reference Code - MRC
        SA - PCIe Version
        SA-CRID Status
--
        Lan Phy Version
        Sensor Firmware Version
        Debug Mode Status
        Disabled
        Performance Mode Status
ubuntu@ubuntu:~$ sudo dmidecode --type 39
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.

##############################

$ cat /proc/driver/rtc | grep batt
batt_status    : okay

#######################################
ubuntu@ubuntu:~$ sudo memtester 20G 5
memtester version 4.3.0 (64-bit)
Copyright (C) 2001-2012 Charles Cazabon.
Licensed under the GNU General Public License version 2 (only).

pagesize is 4096
pagesizemask is 0xfffffffffffff000
want 20480MB (21474836480 bytes)
got  20480MB (21474836480 bytes), trying mlock ...locked.
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
###################

sudo nvme smart-log /dev/nvme0n1
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 49 C
available_spare                     : 100%
available_spare_threshold           : 10%
percentage_used                     : 2%
data_units_read                     : 21,444,800
data_units_written                  : 46,954,603
host_read_commands                  : 382,023,674
host_write_commands                 : 424,999,135
controller_busy_time                : 2,176
power_cycles                        : 3,571
power_on_hours                      : 2,430
unsafe_shutdowns                    : 166
media_errors                        : 0
num_err_log_entries                 : 25
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Temperature Sensor 1                : 49 C
Temperature Sensor 2                : 51 C
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0

################################

$ ./gpu_burn -d 3600
GPU 0: NVIDIA GeForce GTX 1070 (UUID: GPU-98bf2a5b-636b-5cbe-cc66-cdf024b8a920)
Initialized device 0 with 8111 MB of memory (7469 MB available, using 6722 MB of it), using DOUBLES
Results are 33554432 bytes each, thus performing 208 iterations
10.1%  proc'd: 4160 (187 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:03:52 AM EDT

20.2%  proc'd: 8112 (180 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:09:56 AM EDT

30.3%  proc'd: 11856 (178 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:15:57 AM EDT

40.4%  proc'd: 15600 (176 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:22:01 AM EDT

50.4%  proc'd: 19136 (175 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:28:03 AM EDT

60.6%  proc'd: 22880 (172 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:34:08 AM EDT

70.7%  proc'd: 26416 (172 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:40:13 AM EDT

80.8%  proc'd: 29952 (147 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:46:14 AM EDT

90.9%  proc'd: 33280 (158 Gflop/s)   errors: 0   temps: 90 C 
    Summary at:   Thu 01 Jul 2021 05:52:19 AM EDT

100.0%  proc'd: 36192 (158 Gflop/s)   errors: 0   temps: 90 C 
Killing processes.. Freed memory for dev 0
Uninitted cublas
done

Tested 1 GPUs:
    GPU 0: OK








```


Sorry, cannot attached the file since it is too big.

I am wondering what might have caused this. I thought might have something to do with the power supply. I checked the battery (CMOS?)

```

$ cat /proc/driver/rtc | grep batt
batt_status    : okay
```


It would be of great help if someone can shed some light on what happened. Right now everything works normally, keeping my fingers crossed.

---

### Post by Autodave on 2021-07-01
Beeping followed by a shutdown would normally have me looking at the RAM chips.  If you have more that one RAM chip in there, try removing one of them and just running with one.  If OK that way, swap them and see if problem returns.

---

### Post by monkeybrain20122 on 2021-07-01
> **Autodave said:**
> Beeping followed by a shutdown would normally have me looking at the RAM chips.  If you have more that one RAM chip in there, try removing one of them and just running with one.  If OK that way, swap them and see if problem returns.

Hi, but my memtester results look ok (see report)

---

### Post by QIII on 2021-07-01
I'd still try the memory module experiment as a "rule out" in diagnosis.

The irregular nature of the shutdowns -- and the beep from the hardware -- suggests either trouble with memory modules, a thermal fault, a capacitor failure or a power supply failure.  If your CPU temperature is good, there are still hundreds of components that could be failing.

Do the shutdowns ever occur just after starting the machine or during the POST, or only after you reach userland?

---

### Post by TheFu on 2021-07-01
Check the system logs.  Note the time so you know when to look by the timestamp.  Not all hardware issues will make it to a log, but many will.
```
journalctl -xe            # See errors for last service
journalctl -b -1          # See prior boot log
journalctl -b -3          # See 3 boot logs ago
journalctl -b             # See current boot log
journalctl -S today       # See logs for today, from midnight
journalctl -xe -S today   # See errors for today, from midnight
```

---

### Post by CatKiller on 2021-07-01
My inclination would be that it's cracked solder somewhere.

It's worth getting in touch with System76 about it

---

### Post by ActionParsnip on 2021-07-01
I'm betting blown capacitors. Do make sure you have the latest BIOS. If you enter the BIOS and flick around, does it shut down in the same manner? If it does then this is not an Ubuntu issue

---

### Post by monkeybrain20122 on 2021-07-01
> **QIII said:**
> 

Do the shutdowns ever occur just after starting the machine or during the POST, or only after you reach userland?

It happened after I reached userland, never just after I start.  but with the live usb it shut down before (since it takes a lot longer to boot?)

---

### Post by TheFu on 2021-07-01
I've seen both cracked solder and blown capacitors over the decades.  I haven't seen any blown capacitors from name-brand MBs purchased in 2003 or later. Had a dual CPU MB fail with about 15 blown capacitors.  They were easy to spot.  Look at the tops of each for a brown liquid. There shouldn't be any.

For the bad solder connections, the problem could be anywhere. Had one that was traced to the power circuit. The "approved" fix was to replace the $600 motherboard on a $750 laptop.  Insurance bought me a replacement which was a generation newer, 3x faster and I'm still using that 2011 laptop today.

On another, it was the built-in NIC that had a short.  Everything else worked, but whenever code was checked into the central repository, it was majorly corrupted. Fortunately, there were 20 other people with copies of the code who weren't having any issues, so we easily traced back to the machine causing the issue and a warranty replacement was shipped by the PC vendor.  In the meantime, we installed a PCI NIC and disabled the onboard NIC, so that programmer could keep working.

A solder issue as described is unlikely to be user serviceable, unless your eyes just happen to find it or you can "feel" a loose connection.  10 seconds with a hot soldering iron on the loose connection, carefully redoing just a bad connection and not causing any new shorts or frying the components would be necessary.  Where I live, the price to fix it would be more than the cost of a new motherboard, assuming they found the problem quickly.  In some parts of the world, the fix would be very cheap and would make a better-than-new connection.

---

### Post by monkeybrain20122 on 2021-07-01
> **ActionParsnip said:**
> I'm betting blown capacitors. Do make sure you have the latest BIOS. If you enter the BIOS and flick around, does it shut down in the same manner? If it does then this is not an Ubuntu issue

No I don't think it is a Ubuntu issue since it happened to the live usb  too when that happened. The BIOS didn't shut down though,

---

### Post by grahammechanical on 2021-07-01
The motherboard manual might have a section that explains what the bleeps mean.

Regards

---

### Post by Doug S on 2021-07-02
For your i7-7820HK processor, I would run turbostat in some terminal always, suggest this, or similar, command:

```
$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 6
```

For the comment about it being 50 degrees please be aware that processor package temperature can change extremely fast. I have measured (oh darn I can't find it now) over 100 degrees per second. I am saying it is easy to miss a thermal event entirely if only casually observing temperatures. As a test try disabling turbo in BIOS. This will keep temperatures lower and timing margins wider, and is perhaps why you got further on battery sometimes.

---

### Post by him610 on 2021-07-02
While my daughter was using my wife's System76 laptop today, I heard it beep (loud beep). I had never heard it beep before; however, she explained it was triggered by a low battery. Sounded reasonable to me.
+Post #11 by grahammechanical

---

