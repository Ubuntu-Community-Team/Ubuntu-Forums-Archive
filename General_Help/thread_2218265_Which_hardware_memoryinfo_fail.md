---
title: "Which hardware? memory/info fail"
date: 2014-04-20
forum: General Help
---

### Post by Barkester on 2014-04-20
My computer has had a weird week. Its given me the long unending beep as well as the 5 long. Once it even turned the fan on overdrive at reboot. Crashes sometimes.

I did the usual removing of the RAM and put them back 4 times, cleaned it up, but no avail. Its working now, but System Testing says memory/info fails.

I checked the command line apps and the numbers don't match, so I'm not sure which memory its talking about. RAM? Drive? SWAP? VCard? Probly I need some hardware, but what?

  Here's some data from the:

  System tester >  memory/info  Meminfo total: 1804860 kB DMI total: 3072000 kB Accuracy: 58.00 Memory totals not close enough 

```
  $ sudo dmidecode -t memory
[sudo] password for barkester: 
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0030, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0031, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: Flash Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 1

Handle 0x0032, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0030
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: 1
    Locator: XMM1
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 667 MHz
    Manufacturer: JEDEC ID:2C 00 00 00 00 00 00 00
    Serial Number: 6C7F25D8
    Asset Tag: Not Specified
    Part Number: 8HTF6464AY-667B8

Handle 0x0033, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0030
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: 1
    Locator: XMM2
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 667 MHz
    Manufacturer: JEDEC ID:2C 00 00 00 00 00 00 00
    Serial Number: 9FDE18E1
    Asset Tag: Not Specified
    Part Number: 8HTF6464AY-667B8

Handle 0x0034, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0030
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: 2
    Locator: XMM3
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer: JEDEC ID:7F 7F 7F 0B 00 00 00 00
    Serial Number: 7904A92D
    Asset Tag: Not Specified
    Part Number: NT512T64U88A0BY-37

Handle 0x0035, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0030
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: 2
    Locator: XMM4
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer: JEDEC ID:7F 7F 7F 0B 00 00 00 00
    Serial Number: 74257ABB
    Asset Tag: Not Specified
    Part Number: NT512T64U88A0BY-37

Handle 0x0037, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0031
    Error Information Handle: Not Provided
    Total Width: 2 bits
    Data Width: 2 bits
    Size: 1024 kB
    Form Factor: Chip
    Set: None
    Locator: SYSTEM ROM
    Bank Locator: Not Specified
    Type: Flash
    Type Detail: Non-Volatile
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9600B Quad-Core Processor
stepping    : 3
microcode    : 0x1000083
cpu MHz        : 1150.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips    : 4587.27
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9600B Quad-Core Processor
stepping    : 3
microcode    : 0x1000083
cpu MHz        : 1150.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips    : 4587.27
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9600B Quad-Core Processor
stepping    : 3
microcode    : 0x1000083
cpu MHz        : 1150.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips    : 4587.27
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9600B Quad-Core Processor
stepping    : 3
microcode    : 0x1000083
cpu MHz        : 1150.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips    : 4587.27
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```

   Thanks for any info. All I'm sure of is its NOT either OS. Grub maybe if I'm lucky, but looks like hardware to me. All suggestions appreciated.

---

### Post by coldcritter64 on 2014-04-20
> **Barkester said:**
> My computer has had a weird week. Its given me the long unending beep as well as the 5 long. Once it even turned the fan on overdrive at reboot. Crashes sometimes...

Those beeps are hardware fault codes from BIOS usually. What is the make of the Motherboard? 
_*Check the manufactures website or your motherboard manual*_, if you have one, [U][I]for the meaning of those beeps.
[/I][/U]            
 Sounds like you may have some sick hardware there. You make be able to re-seat or adjust specific components to fix it if you find out what those beeps mean, or it could be you need to replace failing components.

---

### Post by Barkester on 2014-04-25
Sorry I'm so slow to reply. Its a AMD Phenom(tm) 9600B Quad-Core Processor × 4 so far as CPU running in a home-assembled computer of second hand parts. 

 I did check the beep codes already, but the warnings both assure me the motherboard is destroyed according to documentation, but actually usually means the RAM want a leg stretch, which I did and its working.

  Still getting that memory/info failure according to the System Testing app though, so something else may be up. ALL other checks are fine.

  Really, I just need to know what the app means by memory/info.Usta think I knew what memory meant, but every memory I check from drives to RAM are fine.

  Can anyone define memory/info for me as used by Sytem Tester?

   Thanks for any replies.

---

