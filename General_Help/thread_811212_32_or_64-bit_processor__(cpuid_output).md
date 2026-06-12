---
title: "32 or 64-bit processor?  (cpuid output)"
date: 2008-05-28
forum: General Help
---

### Post by Phoenix Rising on 2008-05-28
I'm trying to determine if this computer has a 32-bit or 64-bit processor.  It's a Pentium 4, 2.80ghz chip, but beyond that I don't have the documentation that came with the chip and board when I built this thing several years ago.

Following advice on another post, I got cpuid running, and am pasting the output below:

```
 
 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
00000001 00000f29 01020809 00004400 bfebfbff
00000002 665b5001 00000000 00000000 007b7040
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 20202020 20202020 20202020 6e492020
80000003 286c6574 50202952 69746e65 52286d75
80000004 20342029 20555043 30382e32 007a4847

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 00000f29:
Type 0 - Original OEM
Family 15 - Pentium 4
Extended family 0
Model 2 - 
Stepping 9
Reserved 0

Brand index: 9 [not in table]
Extended brand string: "              Intel(R) Pentium(R) 4 CPU 2.80GHz"
CLFLUSH instruction cache line size: 8
Initial APIC ID: 1
Hyper threading siblings: 2

Feature flags bfebfbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
50: Instruction TLB: 4KB and 2MB or 4MB pages, 64 entries
5b: Data TLB: 4KB and 4MB pages, 64 entries
66: 1st-level data cache: 8KB, 4-way set assoc, 64 byte line size
40: No 2nd-level cache, or if 2nd-level cache exists, no 3rd-level cache
70: Trace cache: 12K-micro-op, 4-way set assoc
7b: 2nd-level cache: 512KB, 8-way set assoc, sectored, 64 byte line size
```

I **do** see "64 byte line size" on the last line, but is that a definitive answer as to whether or not this thing's a 64-bit chip?  It's been a very long time since my intro to assembly language class so most of this is greek to me (hey, I write code in Ruby!).  Can you tell me where to look to see if this is 32 or 64 bit - aka, "how to read cpuid output"?

Thanks :)

---

### Post by jrusso2 on 2008-05-28
all Pentium 4's are 32 bit.  I think the core2duo is the first Intel x86 64 cpu.  Itanium was previous but its a risc cpu

---

### Post by sdennie on 2008-05-28
> **jrusso2 said:**
> all Pentium 4's are 32 bit.  I think the core2duo is the first Intel x86 64 cpu.  Itanium was previous but its a risc cpu

Wikipedia thinks they supported EMT64 starting in 2004: [http://en.wikipedia.org/wiki/Pentium_4](http://en.wikipedia.org/wiki/Pentium_4).  I'm not sure how to detect if a CPU is 64bit capable but, one thing that is sure to work is to download a 64bit Ubuntu LiveCD and simply trying to boot from it.

---

