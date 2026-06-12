---
title: "cpu and kernel opts"
date: 2007-09-13
forum: General Help
---

### Post by Eagleon on 2007-09-13
hi, I have been trying to compile my own kernel for the first time ever, and was a little unsure about what options to use for my hardware. I want to get the best performance from the kernel... 

here is my cpuid
>  cpuid
 eax in    eax      ebx      ecx      edx
00000000 0000000a 756e6547 6c65746e 49656e69
00000001 000006f6 01020800 0000e3bd bfebfbff
00000002 05b0b101 005657f0 00000000 2cb43049
00000003 00000000 00000000 00000000 00000000
00000004 04000121 01c0003f 0000003f 00000001
00000005 00000040 00000040 00000003 00022220
00000006 00000001 00000002 00000001 00000000
00000007 00000000 00000000 00000000 00000000
00000008 00000400 00000000 00000000 00000000
00000009 00000000 00000000 00000000 00000000
0000000a 07280202 00000000 00000000 00000000
80000000 80000008 00000000 00000000 00000000
80000001 00000000 00000000 00000001 20000000
80000002 65746e49 2952286c 726f4320 4d542865
80000003 43203229 20205550 20202020 54202020
80000004 30303237 20402020 30302e32 007a4847
80000005 00000000 00000000 00000000 00000000
80000006 00000000 00000000 10008040 00000000
80000007 00000000 00000000 00000000 00000000
80000008 00003024 00000000 00000000 00000000

Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 000006f6:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 15 - 
Extended model 0
Stepping 6
Reserved 0

Extended brand string: "Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz"
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
b1: unknown TLB/cache descriptor
b0: unknown TLB/cache descriptor
05: unknown TLB/cache descriptor
f0: unknown TLB/cache descriptor
57: unknown TLB/cache descriptor
56: unknown TLB/cache descriptor
49: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
b4: unknown TLB/cache descriptor
2c: unknown TLB/cache descriptor
Processor serial: 0000-06F6-0000-0000-0000-0000


seems like a great processor to me :D ... but how can i get the best out of it based on the kernel opts.

All help will be greatly appriciated... thank you in advance

(one more thing... my system is a Toshiba Protege M400 tablet... intel graphics card, 1gb ram, etc...)

---

