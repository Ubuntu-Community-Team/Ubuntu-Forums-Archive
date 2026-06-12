---
title: "Lenovo Laptop &gt; Unable to access BIOS / install Linux properly &gt;"
date: 2024-02-29
forum: General Help
---

### Post by noobtechninja on 2024-02-29
Hi there Guys.

I was really hoping that you could help me with an issue I've been dealing with.

**Background:**
I'm trying to help a friend with their old laptop.
It was originally running Windows 8, then Windows 10.
They REALLY want to play an old Windows XP game (Zoo Tycoon 2).

My intention was to:
1. Wipe the HDD
2. Install Linux (Ubuntu 22.04  LTS)
3. Intall WINE
4. Install the game.

However, there are some complications with this -

The Laptop's keyboard and trackpad are unresponsive / don't work.
Although plugging in an external keyboard and mouse works well.


**Issue:**
I cannot access the BIOS / EUFI on the laptop.
I cannot access secure boot.


**Troubleshooting / Steps already taken:**

1. I have rebooted the laptop (at least 15+ times) trying various different ways
to access the BIOS (Using the F2 / F12 keys) and using the dedicated
novo key (located near the power button).

N.B. I cannot press Fn+F2 as I'm using an external keyboard.

Each time I get to the BIOS selection screen - Chosing any option
(BIOS / Boot selection / etc, etc). will make the laptop boot into the main OS
(Windows 10).

It seems nothing will let me access / enter the BIOS.


2. Removed the HDD from the laptop and connected it to my HDD reader on my own PC.

3. Booted into a live version of Ubuntu 22.04, then using Kparted
deleted the main Windows C: drive and the data drive

However I decided to leave the Windows recovery partitions, EFI, and some other
extra Windows partions still there (in case I need to restore Windows).

4. I then installed Ubuntu 22.04 to the laptopns HDD
Using seperate / (300 GB) and /home (500 GB) partions.

5. Putting the HDD back into the Laptop, it failed to boot into Linux.
But still seeing the Windows recovery partions, attempts to restore the Windows 8
OS back onto the HDD.

6. Tried numerous settings / advanced settings from a basic recovery screen
and it still will not allow be to access the BIOS.


**Questions:**

1. How can I access the BIOS / EUFI ?

2. If I can get into the BIOS, do I need to disable secure boot, to allow me
to install other OS's ?

3. Do I need to re-install Windows 8, to allow me to disable secure boot ?

4. Is there any other way to access and disable secure boot via Linux / Live CD / USB ?

5. Is there anything else that I need to do, or be aware of. In order to fix
this and get Linux installed correctly ?


TIA for any help or advice.

**Laptop details:**
Model: Lenovo G580
CPU: Core i3
HDD: 1 TB HDD (spinning HDD not SSD)
RAM: 4-8 GB

---

### Post by tea for one on 2024-02-29
> **noobtechninja said:**
> 
1. How can I access the BIOS / EUFI 
Remove the internal disk from the laptop
Boot into a live "Try Ubuntu" session using your Ubuntu 22.04 install usb
Open a terminal and enter
```
sudo systemctl reboot --firmware-setup
```

---

### Post by noobtechninja on 2024-03-02
Hi there Tea for One

1. I was able to boot into a live USB and run the code you mentioned.

The code "seemed" to be actioned, and then the bash cursor returned to a standard prompt
awaiting the next instruction.

However, when I then rebooted the laptop, it powers on, the screen is activated
but it sits at a black screen for what seems like forever (I left it there for a good 10-15 mins)
and nothing further happened.

I was not able to get any further, or access the BIOS /EUFI at all.



2. I then ran the following code to gather some information on the BIOS and it's status.

2.1.
```
dmidecode | more
```

2.2 Results =

```
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.
65 structures occupying 2706 bytes.
Table at 0xDAE89000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
       Vendor: LENOVO
       Version: 62CN96WW
       Release Date: 05/06/2013
       Address: 0xE0000
       Runtime Size: 128 kB
       ROM Size: 4 MB
       Characteristics:
               PCI is supported
               BIOS is upgradeable
               BIOS shadowing is allowed
               Boot from CD is supported
               Selectable boot is supported
               EDD is supported
               Print screen service is supported (int 5h)
               8042 keyboard services are supported (int 9h)
               Serial services are supported (int 14h)
               Printer services are supported (int 17h)
               CGA/mono video services are supported (int 10h)
               NEC PC-98
               ACPI is supported
               USB legacy is supported
               BIOS boot specification is supported
               Function key-initiated network boot is supported
               Targeted content distribution is supported
               UEFI is supported
       BIOS Revision: 1.150
       Firmware Revision: 1.57

Handle 0x0001, DMI type 1, 27 bytes
System Information
       Manufacturer: LENOVO
       Product Name: 26899JG
       Version: Lenovo G580
       Serial Number: WB12070405WB03062704
       UUID: 808fcd8a-b0df-e211-a835-a4e0e81cd97a
       Wake-up Type: Other
       SKU Number: 26899
       Family: ChiefRiver System

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
       Manufacturer: LENOVO
       Product Name: Lenovo G580
       Version: 31900003WIN8 STD MLT
       Serial Number: WB12070405
       Asset Tag: No Asset Tag
       Features:
               Board is a hosting board
               Board is replaceable
       Location In Chassis: Part Component
       Chassis Handle: 0x0000
       Type: Motherboard
       Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
       Manufacturer: LENOVO
       Type: Notebook
       Lock: Not Present
       Version: Lenovo G580
       Serial Number: WB12070405
       Asset Tag: No Asset Tag
       Boot-up State: Safe
       Power Supply State: Safe
       Thermal State: Other
       Security Status: Other
       OEM Information: 0x00000000
       Height: Unspecified
       Number Of Power Cords: 1
       Contained Elements: 0
       SKU Number: System SKUNumber

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
       Socket Designation: CPU Socket - U3E1
       Type: Central Processor
       Family: Celeron
       Manufacturer: Intel(R) Corporation
       ID: A9 06 03 00 FF FB EB BF
       Signature: Type 0, Family 6, Model 58, Stepping 9
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
       Version: Intel(R) Celeron(R) CPU 1000M @ 1.80GHz
       Voltage: 0.8 V
       External Clock: 100 MHz
       Max Speed: 1800 MHz
       Current Speed: 1800 MHz
       Status: Populated, Enabled
       Upgrade: Socket rPGA988B
       L1 Cache Handle: 0x0006
       L2 Cache Handle: 0x0007
       L3 Cache Handle: 0x0008
       Serial Number: To Be Filled By O.E.M.
       Asset Tag: To Be Filled By O.E.M.
       Part Number: To Be Filled By O.E.M.
       Core Count: 2
       Core Enabled: 2
       Thread Count: 2
       Characteristics:
               64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
       Socket Designation: L1-Cache
       Configuration: Enabled, Not Socketed, Level 1
       Operational Mode: Write Through
       Location: Internal
       Installed Size: 32 kB
       Maximum Size: 32 kB
       Supported SRAM Types:
               Unknown
       Installed SRAM Type: Unknown
       Speed: Unknown
       Error Correction Type: Parity
       System Type: Data
       Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
       Socket Designation: L1-Cache
       Configuration: Enabled, Not Socketed, Level 1
       Operational Mode: Write Through
       Location: Internal
       Installed Size: 32 kB
       Maximum Size: 32 kB
       Supported SRAM Types:
               Unknown
       Installed SRAM Type: Unknown
       Speed: Unknown
       Error Correction Type: Parity
       System Type: Instruction
       Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
       Socket Designation: L2-Cache
       Configuration: Enabled, Not Socketed, Level 2
       Operational Mode: Write Through
       Location: Internal
       Installed Size: 256 kB
       Maximum Size: 256 kB
       Supported SRAM Types:
               Unknown
       Installed SRAM Type: Unknown
       Speed: Unknown
       Error Correction Type: Multi-bit ECC
       System Type: Unified
       Associativity: 8-way Set-associative

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
       Socket Designation: L3-Cache
       Configuration: Enabled, Not Socketed, Level 3
       Operational Mode: Write Back
       Location: Internal
       Installed Size: 2 MB
       Maximum Size: 2 MB
       Supported SRAM Types:
               Unknown
       Installed SRAM Type: Unknown
       Speed: Unknown
       Error Correction Type: Multi-bit ECC
       System Type: Unified
       Associativity: 8-way Set-associative

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: Keyboard
       External Connector Type: PS/2
       Port Type: Keyboard Port

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: Mouse
       External Connector Type: PS/2
       Port Type: Mouse Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: Other
       External Reference Designator: COM 1
       External Connector Type: DB-9 male
       Port Type: Serial Port 16550A Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB3.0 - 1#/USB2.0 - 1#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB3.0 - 2#/USB2.0 - 2#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB3.0 - 3#/USB2.0 - 3#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB3.0 - 4#/USB2.0 - 4#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 5#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 6#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 7#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 8#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 9#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 10#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 11#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 12#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 13#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: USB2.0 - 14#
       External Connector Type: Access Bus (USB)
       Port Type: USB

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: Ethernet
       External Connector Type: RJ-45
       Port Type: Network Port

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: SATA Port 1 J8J1
       Internal Connector Type: SAS/SATA Plug Receptacle
       External Reference Designator: None
       External Connector Type: None
       Port Type: SATA

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: SATA Port 2 J7G1
       Internal Connector Type: SAS/SATA Plug Receptacle
       External Reference Designator: None
       External Connector Type: None
       Port Type: SATA

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: SATA Port 3(ODD) J9E7
       Internal Connector Type: SAS/SATA Plug Receptacle
       External Reference Designator: None
       External Connector Type: None
       Port Type: SATA

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: eSATA Port 1 J6J1
       External Connector Type: SAS/SATA Plug Receptacle
       Port Type: SATA

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: eSATA Port 2 J7J1
       External Connector Type: SAS/SATA Plug Receptacle
       Port Type: SATA

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
       Internal Reference Designator: None
       Internal Connector Type: None
       External Reference Designator: SATA Port 6(Docking)
       External Connector Type: SAS/SATA Plug Receptacle
       Port Type: SATA

Handle 0x0023, DMI type 9, 17 bytes
System Slot Information
       Designation: PEG Gen1/Gen2/Gen3 X16
       Type: x16 PCI Express
       Current Usage: Available
       Length: Long
       ID: 0
       Characteristics:
               3.3 V is provided
               Opening is shared
               PME signal is supported
       Bus Address: 0000:00:00.0

Handle 0x0024, DMI type 9, 17 bytes
System Slot Information
       Designation: PCI-Express 1 X1
       Type: x1 PCI Express
       Current Usage: Available
       Length: Short
       ID: 1
       Characteristics:
               3.3 V is provided
               Opening is shared
               PME signal is supported
       Bus Address: 0000:00:00.0

Handle 0x0025, DMI type 9, 17 bytes
System Slot Information
       Designation: PCI-Express 2 X1
       Type: x1 PCI Express
       Current Usage: In Use
       Length: Short
       ID: 2
       Characteristics:
               3.3 V is provided
               Opening is shared
               PME signal is supported
       Bus Address: 0000:00:00.0

Handle 0x0026, DMI type 9, 17 bytes
System Slot Information
       Designation: PCI-Express 3 X1
       Type: x1 PCI Express
       Current Usage: Available
       Length: Short
       ID: 3
       Characteristics:
               3.3 V is provided
               Opening is shared
               PME signal is supported
       Bus Address: 0000:00:00.0

Handle 0x0027, DMI type 9, 17 bytes
System Slot Information
       Designation: PCI-Express 4 X1
       Type: x1 PCI Express
       Current Usage: In Use
       Length: Short
       ID: 4
       Characteristics:
               3.3 V is provided
               Opening is shared
               PME signal is supported
       Bus Address: 0000:00:00.0

Handle 0x0028, DMI type 9, 17 bytes
System Slot Information
       Designation: PCI-Express 5 X4
       Type: x4 PCI Express
       Current Usage: Available
       Length: Short
       ID: 5
       Characteristics:
               3.3 V is provided
               Opening is shared
               PME signal is supported
       Bus Address: 0000:00:00.0

Handle 0x0029, DMI type 10, 6 bytes
On Board Device Information
       Type: Video
       Status: Enabled
       Description: Intel(R) Extreme Graphics 3 Controller

Handle 0x002A, DMI type 10, 6 bytes
On Board Device Information
       Type: Sound
       Status: Enabled
       Description: Intel(R) Azalia Audio Device

Handle 0x002C, DMI type 12, 5 bytes
System Configuration Options

Handle 0x002D, DMI type 13, 22 bytes
BIOS Language Information
       Language Description Format: Abbreviated
       Installable Languages: 7
               enUS
               frFR
               jaJP
               koKR
               zhCA
               zhCA
               ruRU
       Currently Installed Language: enUS

Handle 0x003F, DMI type 15, 81 bytes
System Event Log
       Area Length: 18 bytes
       Header Start Offset: 0x0000
       Header Length: 16 bytes
       Data Start Offset: 0x0010
       Access Method: General-purpose non-volatile data functions
       Access Address: 0x00F0
       Status: Valid, Not Full
       Change Token: 0x00000000
       Header Format: Type 1
       Supported Log Type Descriptors: 29
       Descriptor 1: Single-bit ECC memory error
       Data Format 1: Multiple-event handle
       Descriptor 2: Multi-bit ECC memory error
       Data Format 2: Multiple-event handle
       Descriptor 3: Parity memory error
       Data Format 3: None
       Descriptor 4: Bus timeout
       Data Format 4: None
       Descriptor 5: I/O channel block
       Data Format 5: None
       Descriptor 6: Software NMI
       Data Format 6: None
       Descriptor 7: POST memory resize
       Data Format 7: None
       Descriptor 8: POST error
       Data Format 8: POST results bitmap
       Descriptor 9: PCI parity error
       Data Format 9: None
       Descriptor 10: PCI system error
       Data Format 10: None
       Descriptor 11: CPU failure
       Data Format 11: None
       Descriptor 12: EISA failsafe timer timeout
       Data Format 12: None
       Descriptor 13: Correctable memory log disabled
       Data Format 13: None
       Descriptor 14: Logging disabled
       Data Format 14: None
       Descriptor 15: System limit exceeded
       Data Format 15: None
       Descriptor 16: Asynchronous hardware timer expired
       Data Format 16: None
       Descriptor 17: System configuration information
       Data Format 17: None
       Descriptor 18: Hard disk information
       Data Format 18: None
       Descriptor 19: System reconfigured
       Data Format 19: None
       Descriptor 20: Uncorrectable CPU-complex error
       Data Format 20: None
       Descriptor 21: Log area reset/cleared
       Data Format 21: None
       Descriptor 22: System boot
       Data Format 22: None
       Descriptor 23: OEM-specific
       Data Format 23: None
       Descriptor 24: OEM-specific
       Data Format 24: None
       Descriptor 25: OEM-specific
       Data Format 25: None
       Descriptor 26: OEM-specific
       Data Format 26: None
       Descriptor 27: OEM-specific
       Data Format 27: None
       Descriptor 28: OEM-specific
       Data Format 28: None
       Descriptor 29: OEM-specific
       Data Format 29: None

Handle 0x0030, DMI type 18, 23 bytes
32-bit Memory Error Information
       Type: OK
       Granularity: Unknown
       Operation: Unknown
       Vendor Syndrome: Unknown
       Memory Array Address: Unknown
       Device Address: Unknown
       Resolution: Unknown

Handle 0x0031, DMI type 21, 7 bytes
Built-in Pointing Device
       Type: Mouse
       Interface: PS/2
       Buttons: 2

Handle 0x002E, DMI type 22, 26 bytes
Portable Battery
       Location: Rear
       Manufacturer: Intel Corp.
       Manufacture Date: 2008
       Serial Number: 1.0
       Name: Smart Battery
       Design Capacity: Unknown
       Design Voltage: Unknown
       SBDS Version: V1.0
       Maximum Error: Unknown
       SBDS Chemistry: Lithium-Ion
       OEM-specific Information: 0x00000000

Handle 0x0032, DMI type 23, 13 bytes
System Reset
       Status: Disabled
       Watchdog Timer: Present
       Boot Option: Do Not Reboot
       Boot Option On Limit: Do Not Reboot
       Reset Count: Unknown
       Reset Limit: Unknown
       Timer Interval: Unknown
       Timeout: Unknown

Handle 0x0033, DMI type 24, 5 bytes
Hardware Security
       Power-On Password Status: Unknown
       Keyboard Password Status: Unknown
       Administrator Password Status: Unknown
       Front Panel Reset Status: Unknown

Handle 0x0034, DMI type 27, 14 bytes
Cooling Device
       Type: Unknown
       Status: Unknown
       OEM-specific Information: 0x00000090
       Nominal Speed: Unknown Or Non-rotating

Handle 0x002F, DMI type 32, 11 bytes
System Boot Information
       Status: No errors detected

Handle 0x0035, DMI type 39, 22 bytes
System Power Supply
       Location: TBD by ODM
       Name: TBD by ODM
       Manufacturer: TBD by ODM
       Serial Number: TBD by ODM
       Asset Tag: TBD by ODM
       Model Part Number: TBD by ODM
       Revision: 1.0
       Max Power Capacity: Unknown
       Status: Present, OK
       Type: Battery
       Input Voltage Range Switching: Other
       Plugged: Yes
       Hot Replaceable: Yes

Handle 0x0009, DMI type 129, 8 bytes
OEM-specific Type
       Header and Data:
               81 08 09 00 01 01 02 01
       Strings:
               Intel_ASF
               Intel_ASF_001

Handle 0x000A, DMI type 131, 64 bytes
OEM-specific Type
       Header and Data:
               83 40 0A 00 10 00 00 00 00 00 00 00 00 00 00 00
               F8 00 59 1E FF FF FF FF 01 20 00 00 01 00 08 00
               E0 04 00 00 00 00 00 00 C8 00 FF FF 00 00 00 00
               00 00 00 00 20 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x002B, DMI type 133, 5 bytes
OEM-specific Type
       Header and Data:
               85 05 2B 00 01
       Strings:
               KHOIHGIUCCHHII

Handle 0x0036, DMI type 16, 23 bytes
Physical Memory Array
       Location: System Board Or Motherboard
       Use: System Memory
       Error Correction Type: None
       Maximum Capacity: 32 GB
       Error Information Handle: Not Provided
       Number Of Devices: 4

Handle 0x0037, DMI type 17, 34 bytes
Memory Device
       Array Handle: 0x0036
       Error Information Handle: Not Provided
       Total Width: 64 bits
       Data Width: 64 bits
       Size: 2 GB
       Form Factor: SODIMM
       Set: None
       Locator: ChannelA-DIMM0
       Bank Locator: BANK 0
       Type: DDR3
       Type Detail: Synchronous
       Speed: 1600 MT/s
       Manufacturer: Micron
       Serial Number: E98448D5
       Asset Tag: 9876543210
       Part Number: 8KTF25664HZ-1G6M1  
       Rank: Unknown
       Configured Memory Speed: 1600 MT/s

Handle 0x0038, DMI type 17, 34 bytes
Memory Device
       Array Handle: 0x0036
       Error Information Handle: Not Provided
       Total Width: Unknown
       Data Width: Unknown
       Size: No Module Installed
       Form Factor: DIMM
       Set: None
       Locator: ChannelA-DIMM1
       Bank Locator: BANK 1
       Type: Unknown
       Type Detail: None
       Speed: Unknown
       Manufacturer: Not Specified
       Serial Number: Not Specified
       Asset Tag: 9876543210
       Part Number: Not Specified
       Rank: Unknown
       Configured Memory Speed: Unknown

Handle 0x0039, DMI type 17, 34 bytes
Memory Device
       Array Handle: 0x0036
       Error Information Handle: Not Provided
       Total Width: 64 bits
       Data Width: 64 bits
       Size: 4 GB
       Form Factor: SODIMM
       Set: None
       Locator: ChannelB-DIMM0
       Bank Locator: BANK 2
       Type: DDR3
       Type Detail: Synchronous
       Speed: 1600 MT/s
       Manufacturer: Micron
       Serial Number: E375B06D
       Asset Tag: 9876543210
       Part Number: 16KTF51264HZ-1G6M1
       Rank: Unknown
       Configured Memory Speed: 1600 MT/s

Handle 0x003A, DMI type 17, 34 bytes
Memory Device
       Array Handle: 0x0036
       Error Information Handle: Not Provided
       Total Width: Unknown
       Data Width: Unknown
       Size: No Module Installed
       Form Factor: DIMM
       Set: None
       Locator: ChannelB-DIMM1
       Bank Locator: BANK 3
       Type: Unknown
       Type Detail: None
       Speed: Unknown
       Manufacturer: Not Specified
       Serial Number: Not Specified
       Asset Tag: 9876543210
       Part Number: Not Specified
       Rank: Unknown
       Configured Memory Speed: Unknown

Handle 0x003B, DMI type 20, 35 bytes
Memory Device Mapped Address
       Starting Address: 0x00000000000
       Ending Address: 0x000FFFFFFFF
       Range Size: 4 GB
       Physical Device Handle: 0x0037
       Memory Array Mapped Address Handle: 0x003E
       Partition Row Position: 1
       Interleave Position: 1
       Interleaved Data Depth: 2

Handle 0x003C, DMI type 20, 35 bytes
Memory Device Mapped Address
       Starting Address: 0x00000000000
       Ending Address: 0x000FFFFFFFF
       Range Size: 4 GB
       Physical Device Handle: 0x0038
       Memory Array Mapped Address Handle: 0x003E
       Partition Row Position: 1
       Interleave Position: 2
       Interleaved Data Depth: 2

Handle 0x003D, DMI type 20, 35 bytes
Memory Device Mapped Address
       Starting Address: 0x00100000000
       Ending Address: 0x0017FFFFFFF
       Range Size: 2 GB
       Physical Device Handle: 0x0039
       Memory Array Mapped Address Handle: 0x003E
       Partition Row Position: 1

Handle 0x003E, DMI type 19, 31 bytes
Memory Array Mapped Address
       Starting Address: 0x00000000000
       Ending Address: 0x0017FFFFFFF
       Range Size: 6 GB
       Physical Array Handle: 0x0036
       Partition Width: 4

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table
```

---

### Post by tea for one on 2024-03-02
> **noobtechninja said:**
> I was not able to get any further, or access the BIOS /EUFI at all
That's a pity - I was expecting a positive outcome
> **noobtechninja said:**
> The code "seemed" to be actioned, and then the bash cursor returned to a standard prompt
awaiting the next instruction
When you enter the reboot command in a live session, the terminal closes almost instantly, the PC should shutdown quickly and find its way to the UEFI set up pages.
There should not be another prompt in the terminal.

Would you mind trying again?
It might force the electrons of your friend's Lenovo to co-operate.
```
UEFI is supported
```
One bit of good news

---

### Post by noobtechninja on 2024-03-03
I did try your code a few more times.
Each with the same result - The code "appears" to be actioned in the CLI
but nothing else happens, and no reboot is initiated.


So, I have managed to get Linux installed onto this Laptop

I had to use brute force and ignorance (not usually recommended) in these matters.
However I was fed up with secure boot making things much more difficult than
necessary.

In the end, I plugged the laptop's HDD, into my main PC via an external HD reader.

I deleted all the partitions on the laptop's HDD (even the hidden partitions and
the Windows recovery partitions), as these were preventing me from doing anything
useful by continually trying to boot into the Windows recovery process.

I then re-installed the HDD into the laptop, managed to boot from my Ventoy USB
stick, and did a fresh install of Linux.

I still cannot get access to the BIOS / EUFI.
I think secure boot is hampering my efforts.

I've then been able to download and install some Linux apps and Lutris, as this appears
to have the best chance of installing the game (Zoo Tycoon 2).

See guide below:
[https://www.reddit.com/r/ZooTycoon/comments/110iph2/zoo_tycoon_2_linux_installation_guide/](https://www.reddit.com/r/ZooTycoon/comments/110iph2/zoo_tycoon_2_linux_installation_guide/)

Thanks for your help so-far.
It's very much appreciated.

---

### Post by tea for one on 2024-03-04
> **noobtechninja said:**
> I still cannot get access to the BIOS / EUFI.
I think secure boot is hampering my efforts.
You can create a rEFInd Boot Manager installed on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
There is an option [COLOR="#0000FF"]Reboot to Computer Setup Utility[/COLOR]
Worth a shot?

---

### Post by dragonfly41 on 2024-03-04
+1    I was about to suggest rEFInd. My rEFInd GUI shows not only Windows 10, Ubuntu 20.04  and Ubuntu 22.04 (as I migrate 20->22) but also a host of other Dell options including BIOS. Also when Ilast visiting Windows 10 I found an app [EasyUEFI]("https://www.easyuefi.com/index-us.html") which inspects and configures UEFI from Windows session. But after 14 days trial you have to pay. It is Windows world.

---

