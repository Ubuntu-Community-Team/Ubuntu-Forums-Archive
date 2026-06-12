---
title: "Due Kernel I/O error, system refuses to  boot sometimes"
date: 2008-04-21
forum: General Help
---

### Post by gary4gar on 2008-04-21
My system refuses to boot randomly .
here is the error
```
[ 52.308000] ata2.00: exeception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 52.308000] ata2.00: cmd c8/00:08:d6:4a:89/00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
[ 92.568000] ata2.00: revalidation failed (errno=-5)
[ 137.832000] ata2.00: revalidation failed (errno=-5)
```now after this, all process started by init are reporting I/O errors
eg.
> * Running local boot scripts (/etc/rc.local)              [ OK ]
etc/init.rc/: 2:/etc/rc2.d/S99stop=readhead: Input/output error
and lastly i get this message,after this there are no further messages and i am forced to reboot it via REISUB:(

```
Buffer I/O error on device sda2, logical block 0
```[B]
Here is Bit of information about my system
[/B]> 
Amd Athlon 64 3000+
MSI-k8mm-v
1 GB drr 400 RAM
Nvidia 6200 128MB Graphics
Seagate ST380815AS(just 2 months old)
Ubuntu 7.10 x86
Kernel 2.6.22-14-generic

I am dual booting it with Windows xp Sp2.

I suspect this error is related to SATA driver,HDD, SATA II backwards compatibility & sata port on my system.

---

### Post by gary4gar on 2008-04-21
Here is some more information.

```
gaurish@gaurish-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)

```



```
gaurish@gaurish-desktop:~$ cat /proc/version_signature
Ubuntu 2.6.22-14.52-generic

```


smartctl scan results
> 
:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST380815AS
Serial Number:    6RA6TP00
Firmware Version: 3.AAD
User Capacity:    80,026,361,856 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Apr 21 22:58:26 2008 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 430) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  27) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       232852004
  3 Spin_Up_Time            0x0003   099   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       443
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       14672038
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       634
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       461
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       260
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   050   049   045    Old_age   Always       -       841744434
194 Temperature_Celsius     0x0022   050   051   000    Old_age   Always       -       50 (Lifetime Min/Max 0/18)
195 Hardware_ECC_Recovered  0x001a   081   069   000    Old_age   Always       -       128192585
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 276 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 276 occurred at disk power-on lifetime: 339 hours (14 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 24 0d 60 e0  Error: UNC at LBA = 0x00600d24 = 6294820

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 1f 0d 60 e0 00      00:25:54.949  READ DMA EXT
  25 03 01 00 00 00 e0 00      00:25:54.948  READ DMA EXT
  24 03 01 af f8 50 e0 00      00:25:54.947  READ SECTOR(S) EXT
  c6 03 10 af f8 50 a0 00      00:25:54.946  SET MULTIPLE MODE
  91 03 3f af f8 50 af 00      00:25:54.936  INITIALIZE DEVICE PARAMETERS [OBS-6]

Error 275 occurred at disk power-on lifetime: 339 hours (14 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 24 0d 60 e0  Error: UNC at LBA = 0x00600d24 = 6294820

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 1f 0d 60 e0 00      00:25:46.872  READ DMA EXT
  25 03 01 00 00 00 e0 00      00:25:46.871  READ DMA EXT
  25 03 01 00 00 00 e0 00      00:25:46.870  READ DMA EXT
  25 03 01 00 00 00 e0 00      00:25:46.860  READ DMA EXT
  24 03 01 af f8 50 e0 00      00:25:46.857  READ SECTOR(S) EXT

Error 274 occurred at disk power-on lifetime: 339 hours (14 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 24 0d 60 e0  Error: UNC at LBA = 0x00600d24 = 6294820

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 20 1f 0d 60 e0 00      00:25:39.713  READ DMA EXT
  25 03 08 17 0d 60 e0 00      00:25:39.713  READ DMA EXT
  25 03 08 77 ff 9b e0 00      00:25:39.712  READ DMA EXT
  25 03 08 87 ff 9b e0 00      00:25:39.712  READ DMA EXT
  25 03 08 97 0f b0 e0 00      00:25:39.712  READ DMA EXT

Error 273 occurred at disk power-on lifetime: 339 hours (14 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 24 0d 60 e0  Error: UNC at LBA = 0x00600d24 = 6294820

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 80 0f 0d 60 e0 00      00:25:33.053  READ DMA EXT
  24 03 01 af f8 50 e0 00      00:25:33.040  READ SECTOR(S) EXT
  c6 03 10 af f8 50 a0 00      00:25:33.037  SET MULTIPLE MODE
  91 03 3f af f8 50 af 00      00:25:33.027  INITIALIZE DEVICE PARAMETERS [OBS-6]
  ef 03 0c af f8 50 a0 00      00:25:32.995  SET FEATURES [Set transfer mode]

Error 272 occurred at disk power-on lifetime: 339 hours (14 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 24 0d 60 e0  Error: UNC at LBA = 0x00600d24 = 6294820

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 80 0f 0d 60 e0 00      00:25:26.876  READ DMA EXT
  24 03 01 af f8 50 e0 00      00:25:26.792  READ SECTOR(S) EXT
  c6 03 10 af f8 50 a0 00      00:25:20.816  SET MULTIPLE MODE
  91 03 3f af f8 50 af 00      00:25:20.816  INITIALIZE DEVICE PARAMETERS [OBS-6]
  ef 03 0c af f8 50 a0 00      00:25:20.806  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         3         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
gaurish@gaurish-desktop:~$ 




Please post, If anything else is Required

---

### Post by gary4gar on 2008-04-21
Output of dmesg, after rebooting.
Now error message is displayed & system strangely behaves normal:|   
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4b80
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6B80 checksum 0
[    0.000000] ACPI: RSDP 000F6B80, 0014 (r0 VIAK8M)
[    0.000000] ACPI: RSDT 3FFF3040, 002C (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF30C0, 0074 (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF3180, 4D34 (r1 VIAK8M AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF7F00, 005A (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=445bad1a-9af1-4eac-8637-9cfd3b8dcb3d ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1999.806 MHz processor.
[   18.884038] Console: colour VGA+ 80x25
[   18.884512] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.884953] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.906700] Memory: 1027880k/1048512k available (2015k kernel code, 19928k reserved, 915k data, 364k init, 131008k highmem)
[   18.906710] virtual kernel memory layout:
[   18.906711]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.906713]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.906714]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.906715]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.906716]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   18.906717]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   18.906719]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   18.906722] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.906759] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.986784] Calibrating delay using timer specific routine.. 4004.27 BogoMIPS (lpj=8008550)
[   18.986813] Security Framework v1.0.0 initialized
[   18.986822] SELinux:  Disabled at boot.
[   18.986834] Mount-cache hash table entries: 512
[   18.986965] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   18.986973] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.986976] CPU: L2 Cache: 512K (64 bytes/line)
[   18.986978] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   18.986989] Compat vDSO mapped to ffffe000.
[   18.987001] Checking 'hlt' instruction... OK.
[   19.002922] SMP alternatives: switching to UP code
[   19.003129] Freeing SMP alternatives: 11k freed
[   19.003399] Early unpacking initramfs... done
[   19.294738] ACPI: Core revision 20070126
[   19.294816] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.297315] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   19.297337] Total of 1 processors activated (4004.27 BogoMIPS).
[   19.297840] ENABLING IO-APIC IRQs
[   19.298160] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   19.442801] Brought up 1 CPUs
[   19.442926] Booting paravirtualized kernel on bare hardware
[   19.443012] Time: 22:35:57  Date: 03/21/108
[   19.443032] NET: Registered protocol family 16
[   19.443104] EISA bus registered
[   19.443121] ACPI: bus type pci registered
[   19.450686] PCI: PCI BIOS revision 2.10 entry at 0xfb4b0, last bus=1
[   19.450688] PCI: Using configuration type 1
[   19.450690] Setting up standard PCI resources
[   19.455611] ACPI: EC: Look up EC in DSDT
[   19.459740] ACPI: Interpreter enabled
[   19.459746] ACPI: (supports S0 S1 S4 S5)
[   19.459762] ACPI: Using IOAPIC for interrupt routing
[   19.464834] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.464845] PCI: Probing PCI hardware (bus 00)
[   19.465615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.503994] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   19.504128] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   19.504261] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 *12)
[   19.504380] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   19.504496] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   19.504607] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   19.504717] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   19.504828] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   19.504966] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   19.505093] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   19.505220] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   19.505366] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   19.505430] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.505441] pnp: PnP ACPI init
[   19.505448] ACPI: bus type pnp registered
[   19.508537] pnp: PnP ACPI: found 13 devices
[   19.508539] ACPI: ACPI bus type pnp unregistered
[   19.508542] PnPBIOS: Disabled by ACPI PNP
[   19.508584] PCI: Using ACPI for IRQ routing
[   19.508587] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.532951] NET: Registered protocol family 8
[   19.532953] NET: Registered protocol family 20
[   19.533002] pnp: 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   19.533005] pnp: 00:00: iomem range 0xdcc00-0xdffff has been reserved
[   19.533008] pnp: 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[   19.533010] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   19.533015] pnp: 00:02: ioport range 0x4000-0x407f has been reserved
[   19.533018] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   19.534768] Time: tsc clocksource has been installed.
[   19.563244] PCI: Bridge: 0000:00:01.0
[   19.563246]   IO window: disabled.
[   19.563250]   MEM window: f8000000-faffffff
[   19.563253]   PREFETCH window: e0000000-efffffff
[   19.563266] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.563277] NET: Registered protocol family 2
[   19.602811] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.602945] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   19.604517] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.605082] TCP: Hash tables configured (established 131072 bind 65536)
[   19.605085] TCP reno registered
[   19.614892] checking if image is initramfs... it is
[   20.066758] Switched to high resolution mode on CPU 0
[   20.184300] Freeing initrd memory: 7060k freed
[   20.184643] audit: initializing netlink socket (disabled)
[   20.184657] audit(1208817357.024:1): initialized
[   20.184716] highmem bounce pool size: 64 pages
[   20.186091] VFS: Disk quotas dquot_6.5.1
[   20.186130] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.186216] io scheduler noop registered
[   20.186218] io scheduler anticipatory registered
[   20.186219] io scheduler deadline registered
[   20.186233] io scheduler cfq registered (default)
[   20.186246] PCI: VIA PCI bridge detected. Disabling DAC.
[   20.186310] Boot video device is 0000:01:00.0
[   20.186430] isapnp: Scanning for PnP cards...
[   20.540476] isapnp: No Plug & Play device found
[   20.558377] Real Time Clock Driver v1.12ac
[   20.558458] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.558547] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.558690] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.559094] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.559273] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.559393] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
[   20.559587] 0000:00:0a.0: ttyS2 at I/O 0xe008 (irq = 16) is a 16450
[   20.559710] 0000:00:0a.0: ttyS3 at I/O 0xe010 (irq = 16) is a 8250
[   20.559763] Couldn't register serial port 0000:00:0a.0: -28
[   20.560193] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.560339] input: Macintosh mouse button emulation as /class/input/input0
[   20.560393] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   20.560395] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   20.810673] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.810777] mice: PS/2 mouse device common for all mice
[   20.810867] EISA: Probing bus 0 at eisa.0
[   20.810886] Cannot allocate resource for EISA slot 4
[   20.810888] Cannot allocate resource for EISA slot 5
[   20.810901] EISA: Detected 0 cards.
[   20.810985] TCP cubic registered
[   20.810995] NET: Registered protocol family 1
[   20.811014] Using IPI No-Shortcut mode
[   20.811165]   Magic number: 4:928:603
[   20.811224]   hash matches device ptyd7
[   20.811233]   hash matches device ptyaa
[   20.811586] Freeing unused kernel memory: 364k freed
[   20.892052] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.020832] AppArmor: AppArmor initialized<5>audit(1208817358.524:2):  type=1505 info="AppArmor initialized" pid=1202
[   22.027029] fuse init (API version 7.8)
[   22.031607] Failure registering capabilities with primary security module.
[   22.620948] SCSI subsystem initialized
[   22.624855] libata version 2.21 loaded.
[   22.625887] sata_via 0000:00:0f.0: version 2.2
[   22.626121] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   22.626130] ACPI: PCI Interrupt 0000:00:0f.0[b] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   22.626180] sata_via 0000:00:0f.0: routed to hard irq line 11
[   22.626251] scsi0 : sata_via
[   22.626298] scsi1 : sata_via
[   22.626320] ata1: SATA max UDMA/133 cmd 0x0001e100 ctl 0x0001e202 bmdma 0x0001e500 irq 17
[   22.626324] ata2: SATA max UDMA/133 cmd 0x0001e300 ctl 0x0001e402 bmdma 0x0001e508 irq 17
[   22.651758] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.651764] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.690263] usbcore: registered new interface driver usbfs
[   22.690314] usbcore: registered new interface driver hub
[   22.690331] usbcore: registered new device driver usb
[   22.719965] USB Universal Host Controller Interface driver v3.0
[   22.741633] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   22.741638] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   22.830296] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   22.897751] Floppy drive(s): fd0 is 1.44M
[   22.918597] FDC 0 is a post-1991 82077
[   23.042234] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.272598] ata2.00: ATA-7: ST380815AS, 3.AAD, max UDMA/133
[   23.272601] ata2.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.339218] ata2.00: configured for UDMA/133
[   23.339322] scsi 1:0:0:0: Direct-Access     ATA      ST380815AS       3.AA PQ: 0 ANSI: 5
[   23.339726] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   23.339745] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   23.339756] VP_IDE: chipset revision 6
[   23.339757] VP_IDE: not 100% native mode: will probe irqs later
[   23.339767] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   23.339775]     ide0: BM-DMA at 0xe700-0xe707, BIOS settings: hda:pio, hdb:pio
[   23.339786]     ide1: BM-DMA at 0xe708-0xe70f, BIOS settings: hdc:DMA, hdd:pio
[   23.339792] Probing IDE interface ide0...
[   23.356113] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.356125] sd 1:0:0:0: [sda] Write Protect is off
[   23.356128] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.356140] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.356185] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.356191] sd 1:0:0:0: [sda] Write Protect is off
[   23.356193] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.356204] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.356208]  sda: sda1 sda2 sda3
[   23.387658] sd 1:0:0:0: [sda] Attached SCSI disk
[   23.391782] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   23.668747] EXT3-fs: INFO: recovery required on readonly filesystem.
[   23.668752] EXT3-fs: write access will be enabled during recovery.
[   23.681831] kjournald starting.  Commit interval 5 seconds
[   23.681837] EXT3-fs: recovery complete.
[   23.681973] EXT3-fs: mounted filesystem with ordered data mode.
[   23.906101] Probing IDE interface ide1...
[   24.770055] hdc: BENQ DVD DD DW1650, ATAPI CD/DVD-ROM drive
[   25.107205] ide1 at 0x170-0x177,0x376 on irq 15
[   25.109593] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   25.109601] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.109612] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   25.109799] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   25.109826] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000e800
[   25.109951] usb usb1: configuration #1 chosen from 1 choice
[   25.109975] hub 1-0:1.0: USB hub found
[   25.109982] hub 1-0:1.0: 2 ports detected
[   25.213984] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.213993] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   25.214010] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   25.214028] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000e900
[   25.214106] usb usb2: configuration #1 chosen from 1 choice
[   25.214125] hub 2-0:1.0: USB hub found
[   25.214131] hub 2-0:1.0: 2 ports detected
[   25.317981] ACPI: PCI Interrupt 0000:00:10.2[b] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.317991] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   25.318012] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   25.318033] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000ea00
[   25.318116] usb usb3: configuration #1 chosen from 1 choice
[   25.318136] hub 3-0:1.0: USB hub found
[   25.318144] hub 3-0:1.0: 2 ports detected
[   25.421925] ACPI: PCI Interrupt 0000:00:10.3[b] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.421932] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   25.421947] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   25.421965] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000eb00
[   25.422042] usb usb4: configuration #1 chosen from 1 choice
[   25.422061] hub 4-0:1.0: USB hub found
[   25.422068] hub 4-0:1.0: 2 ports detected
[   25.526064] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.526075] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   25.526093] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   25.526131] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfb001000
[   25.526137] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.526204] usb usb5: configuration #1 chosen from 1 choice
[   25.526223] hub 5-0:1.0: USB hub found
[   25.526230] hub 5-0:1.0: 8 ports detected
[   25.630213] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   25.630221] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
[   25.630306] eth0: VIA Rhine II at 0x1ed00, 00:11:09:06:18:c6, IRQ 19.
[   25.631020] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   26.817650] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   26.994645] usb 2-2: configuration #1 chosen from 1 choice
[   28.602085] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.035265] Linux agpgart interface v0.102 (c) Dave Jones
[   30.074983] agpgart: Detected AGP bridge 0
[   30.078904] agpgart: AGP aperture is 128M @ 0xf0000000
[   30.194500] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.294394] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.901302] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   30.901310] Uniform CD-ROM driver Revision: 3.20
[   31.500839] nvidia: module license 'NVIDIA' taints kernel.
[   31.755664] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   31.755880] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   31.776862] input: PC Speaker as /class/input/input2
[   31.791886] parport_pc 00:0b: reported by Plug and Play ACPI
[   31.791938] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   31.809946] usbcore: registered new interface driver hiddev
[   31.822426] input: Microsoft Basic Optical Mouse as /class/input/input3
[   31.822473] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:10.1-2
[   31.822487] usbcore: registered new interface driver usbhid
[   31.822490] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.327174] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   32.327183] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21
[   32.327320] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   33.426746] lp0: using parport0 (interrupt-driven).
[   33.465292] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   33.465330] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
[   33.465332] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[   33.465335] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   33.530884] w83627hf: Found W83627THF chip at 0x290
[   33.532323] w83627hf w83627hf.656: Reading VID from GPIO5
[   33.904174] EXT3 FS on sda2, internal journal
[   34.816100] kjournald starting.  Commit interval 5 seconds
[   34.816253] EXT3 FS on sda3, internal journal
[   34.816258] EXT3-fs: mounted filesystem with ordered data mode.
[   35.901926] input: Power Button (FF) as /class/input/input4
[   35.906141] ACPI: Power Button (FF) [PWRF]
[   35.939259] input: Power Button (CM) as /class/input/input5
[   35.943440] ACPI: Power Button (CM) [PWRB]
[   36.019085] No dock devices found.
[   36.963138] Failure registering capabilities with primary security module.
[   37.215828] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   37.215833] apm: overridden by ACPI.
[   19.512000] Marking TSC unstable due to: cpufreq changes.
[   19.516000] Time: acpi_pm clocksource has been installed.
[   20.440000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   20.440000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   20.440000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   21.556000] ppdev: user-space parallel port driver
[   21.796000] audit(1208797578.220:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4924 profile="/usr/sbin/cupsd"
[   23.552000] Clocksource tsc unstable (delta = -142799059 ns)
```

Please post, If anything else is Required


[edit]
seems the problem is widespread, with no workaround available.
more 10,000 results in Google.
[http://www.google.co.in/search?q=exception+Emask+0x0+SAct+0x0+SErr+0x0+action+0x2+frozen](http://www.google.co.in/search?q=exception+Emask+0x0+SAct+0x0+SErr+0x0+action+0x2+frozen)

---

### Post by oldmanuk on 2008-05-19
same problems, eventually result in / being remounted as read-only (due to errors)

have tried various additions to /proc/cmdline to try and fix it but no joy :(

---

### Post by Octagonal on 2008-05-19
My system occasionally hangs on boot up when I have my usb hard drives plugged in.  But I have nothing to add regarding the sata drives.

---

