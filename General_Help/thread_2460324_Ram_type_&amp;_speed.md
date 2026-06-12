---
title: "Ram type &amp; speed"
date: 2021-04-07
forum: General Help
---

### Post by AnupamMitra on 2021-04-07
The OS in one of my desktops is Ubuntu 18.04.5 32 bit. RAM is 2 GB. Now I would like to upgrade to Ubuntu 20.04. Processor [Pentium(R) Dual-Core CPU E5200 @ 2.50GHz × 2] 
 which is, I think, okay for 64 bit. Graphics is Intel® G33 x86/MMX/SSE2. However the RAM is too low. Therefore, I would like to increase RAM. How do I know the required speed of RAM commensurate with my PC for buying additional Memory? 

However, the output of dmidecode -t 17 is as under.
```


naresh@naresh-G31T-M2:~$ sudo dmidecode -t 17
[sudo] password for naresh: 
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.5 present.

Handle 0x000F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0011, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

naresh@naresh-G31T-M2:~$ 

```

---

### Post by scorp123 on 2021-04-07
About 64-bit or not: Check if you have the "lm" flag ("lm" = "Long Mode" = 64-bit) on your CPU? You can use this command: ```
cat /proc/cpuinfo
```
Example from one of my systems:

```
:~> cat /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 96
model name      : AMD Opteron(tm) X3418 APU
stepping        : 1
microcode       : 0x600611a
cpu MHz         : 3114.451
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 16
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp **[COLOR="#FF0000"]lm[/COLOR]** constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic vgif overflow_recov
bugs            : fxsave_leak sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips        : 3593.35
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro acc_power [13]
```

If the "lm" flag is missing then that CPU is not 64-bit.

---

### Post by deadflowr on 2021-04-07
> How do I know the required speed of RAM commensurate with my PC for buying additional Memory?

Look up information on the motherboard.
Manuals and documentation for this motherboard will tell you the max RAM limits are.
And what speed and/or versions are supported.

The G33 looks like it supports either DDR2 or DDR3,
(I'm sure it's not both at the same time.)
With a max of 8GB, 
with 800MHZ max speed for DDR2
and 1066 max speed for DDR3.

Some reference documentation here: [https://www.intel.com/assets/pdf/prodbrief/317311.pdf]("https://www.intel.com/assets/pdf/prodbrief/317311.pdf")

---

### Post by rsteinmetz70112 on 2021-04-07
What is the motherboard or computer model

---

### Post by kurt18947 on 2021-04-07
Would this be of any use to you? You wouldn't have to buy Crucial memory though I have had good success using it.

[URL="https://www.crucial.com/store/systemscanner"]https://www.crucial.com/store/systemscanner


[/URL] Oops this is a Windows app. Crucial has a memory selector here:

[https://www.crucial.com/store/advisor](https://www.crucial.com/store/advisor)

---

### Post by Yellow Pasque on 2021-04-09
For whatever reason, your memory stick does not properly report its attributes with smbios/dmidecode.
Give the full output of dmidecode:
```
sudo dmidecode
```

---

### Post by rsteinmetz70112 on 2021-04-09
```
# dmidecode
``` with usually report the motherboard brand and model number.

---

### Post by sofasurfer on 2021-04-09
I'd just like to add my 2 cents worth. I just installed 20.04. Its supposed to need at least 4 gigs of ram. I couldn't get the extra ram right now so I just installed it anyway with 2 gigs. It runs perfectly fine.

---

### Post by CelticWarrior on 2021-04-09
> **sofasurfer said:**
> I just installed it anyway with 2 gigs. It runs perfectly fine.
Yes, but you must be very careful about what you're running simultaneously.

---

### Post by AnupamMitra on 2021-04-12
> **scorp123 said:**
> About 64-bit or not: Check if you have the "lm" flag ("lm" = "Long Mode" = 64-bit) on your CPU? You can use this command: ```
cat /proc/cpuinfo
```
Example from one of my systems:

```
:~> cat /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 96
model name      : AMD Opteron(tm) X3418 APU
stepping        : 1
microcode       : 0x600611a
cpu MHz         : 3114.451
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 16
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp **[COLOR=#FF0000]lm[/COLOR]** constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic vgif overflow_recov
bugs            : fxsave_leak sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips        : 3593.35
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro acc_power [13]
```

If the "lm" flag is missing then that CPU is not 64-bit.

Thanks. The outcome of *cat /proc/cpuinfo* is as under. I think it is 64 bit. Isn't it?

```

naresh@naresh-G31T-M2:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping    : 10
microcode    : 0xa0b
cpu MHz        : 1580.895
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm pti dtherm
bugs        : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
bogomips    : 4987.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping    : 10
microcode    : 0xa0b
cpu MHz        : 1534.361
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm pti dtherm
bugs        : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
bogomips    : 4987.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

naresh@naresh-G31T-M2:~$

```

---

### Post by AnupamMitra on 2021-04-12
> **scorp123 said:**
> About 64-bit or not: Check if you have the "lm" flag ("lm" = "Long Mode" = 64-bit) on your CPU? You can use this command: ```
cat /proc/cpuinfo
```
Example from one of my systems:

```
:~> cat /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 21
model           : 96
model name      : AMD Opteron(tm) X3418 APU
stepping        : 1
microcode       : 0x600611a
cpu MHz         : 3114.451
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 16
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp **[COLOR=#FF0000]lm[/COLOR]** constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic vgif overflow_recov
bugs            : fxsave_leak sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips        : 3593.35
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro acc_power [13]
```

If the "lm" flag is missing then that CPU is not 64-bit.

Thanks. The outcome of *cat /proc/cpuinfo* is as under. I think it is 64 bit. Isn't it?

```

naresh@naresh-G31T-M2:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping    : 10
microcode    : 0xa0b
cpu MHz        : 1580.895
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm pti dtherm
bugs        : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
bogomips    : 4987.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping    : 10
microcode    : 0xa0b
cpu MHz        : 1534.361
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm pti dtherm
bugs        : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
bogomips    : 4987.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

naresh@naresh-G31T-M2:~$

```

---

### Post by AnupamMitra on 2021-04-12
> **Yellow Pasque said:**
> For whatever reason, your memory stick does not properly report its attributes with smbios/dmidecode.
Give the full output of dmidecode:
```
sudo dmidecode
```

Thanks for your reply. The outcome of *sudo dmidecode* is as under.

```

naresh@naresh-G31T-M2:~$ sudo dmidecode
[sudo] password for naresh: 
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.5 present.
21 structures occupying 1063 bytes.
Table at 0x000FCE70.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 080014 
    Release Date: 06/20/2008
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
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
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.14

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: HCL Infosystems Limited
    Product Name: G31T-M2
    Version: 1.0
    Serial Number: 8097AZ016909
    UUID: 00020003-0004-0005-0006-000700080009
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: HCL Infosystems Limited
    Product Name: G31T-M2
    Version: 1.0
    Serial Number: 00000000
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: HCL Infosystems Limited
    Type: Desktop
    Lock: Not Present
    Version: 1.0
    Serial Number: 00000000
    Asset Tag: To Be Filled By O.E.M.
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Other
    Manufacturer: Intel            
    ID: 7A 06 01 00 FF FB EB BF
    Version: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz     
    Voltage: 1.3 V
    External Clock: 200 MHz
    Max Speed: 2500 MHz
    Current Speed: 2500 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
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
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 64 kB
    Maximum Size: 64 kB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 2048 kB
    Maximum Size: 2048 kB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 0 kB
    Maximum Size: 0 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0008, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 8192 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 2
        0x0009
        0x000A
    Enabled Error Correcting Capabilities:
        None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 0 1
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 4 5
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x000B, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Abbreviated
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x000C, DMI type 15, 35 bytes
System Event Log
    Area Length: 4 bytes
    Header Start Offset: 0x0000
    Header Length: 2 bytes
    Data Start Offset: 0x0002
    Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
    Access Address: Index 0x046A, Data 0x046C
    Status: Invalid, Not Full
    Change Token: 0x00000000
    Header Format: No Header
    Supported Log Type Descriptors: 6
    Descriptor 1: End of log
    Data Format 1: OEM-specific
    Descriptor 2: End of log
    Data Format 2: OEM-specific
    Descriptor 3: End of log
    Data Format 3: OEM-specific
    Descriptor 4: End of log
    Data Format 4: OEM-specific
    Descriptor 5: End of log
    Data Format 5: OEM-specific
    Descriptor 6: End of log
    Data Format 6: OEM-specific

Handle 0x000D, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x000E, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x000D
    Partition Width: 4

Handle 0x000F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0010, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x000F
    Memory Array Mapped Address Handle: 0x000E
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0011, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Handle 0x0012, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x0011
    Memory Array Mapped Address Handle: 0x000E
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0013, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0014, DMI type 127, 4 bytes
End Of Table

naresh@naresh-G31T-M2:~$

```

---

### Post by Yellow Pasque on 2021-04-12
So your motherboard is ECS G31T-M2. It supports DDR2. (Also, RAM is running at 3.3V, so that's more confirmation that it's DDR2).

As for what speed your current stick of RAM is, it's difficult for us to know because the stick does not report the information. Your best bet is to look in the BIOS. Maybe there could be a label on the stick itself.

If it was me, I would try and find an inexpensive 2GB stick of DDR2-667 and call it a day. Note that even if you have 4GB of RAM, only about 3GB will be usable to the OS, due to integrated graphics and limitations of the G31 chipset.

EDIT: You may also find the RAM speed in your BIOS or on the POST screen when you turn on the computer. To see the speed on the POST screen, you may have to disable the "logo screen" in the BIOS.
The fastest configuration for this system is 2 sticks of 2GB DDR2-800 if that's what you're trying to achieve.

---

### Post by AnupamMitra on 2021-04-17
> **Yellow Pasque said:**
> So your motherboard is ECS G31T-M2. It supports DDR2. (Also, RAM is running at 3.3V, so that's more confirmation that it's DDR2).

As for what speed your current stick of RAM is, it's difficult for us to know because the stick does not report the information. Your best bet is to look in the BIOS. Maybe there could be a label on the stick itself.

If it was me, I would try and find an inexpensive 2GB stick of DDR2-667 and call it a day. Note that even if you have 4GB of RAM, only about 3GB will be usable to the OS, due to integrated graphics and limitations of the G31 chipset.

EDIT: You may also find the RAM speed in your BIOS or on the POST screen when you turn on the computer. To see the speed on the POST screen, you may have to disable the "logo screen" in the BIOS.
The fastest configuration for this system is 2 sticks of 2GB DDR2-800 if that's what you're trying to achieve.

Thanks for your reply. 

As you have suggested, today I checked the labels pasted on the Stick. There are two labels - one by the manufacturer and the other by the importer. Manufacturer's label shows "MT16HTF25664AY-800G1 0923 2GB 2RX8 PC2-6400U-666-13-E0". In the other label it is mentioned "2GB DDRII800 PC2-6400 UNBUFF NON ECC-B".

I think, what you have suggested is appropriate - 2 sticks of 2 GB DDR2-800. 

Now kindly advise me which one I should purchase - 2GB stick of DDR2-667 or 2GB stick of DDR2-800 ?

---

### Post by Yellow Pasque on 2021-04-17
Get another 2GB stick of DDR2-800 as long as it's not expensive.

---

### Post by AnupamMitra on 2021-04-25
> **Yellow Pasque said:**
> Get another 2GB stick of DDR2-800 as long as it's not expensive.

Thank you very much. With your active cooperation I came to know the speed of my RAM and as per your suggestion I installed the second RAM stick (DDR2-800 MHz) yesterday and also installed UBUNTU 64 bit. Now it is completely okay. Thank you again.

---

