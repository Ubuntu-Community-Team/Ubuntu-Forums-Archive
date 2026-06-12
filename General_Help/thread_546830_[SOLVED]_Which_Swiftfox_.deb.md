---
title: "[SOLVED] Which Swiftfox .deb"
date: 2007-09-09
forum: General Help
---

### Post by DougieFresh4U on 2007-09-09
I want to install Swiftfox but the various versions have me a little confused.
I have the Intel Celeron (TM), but the are a few different Celeron
If some one could help out by comparing the info from the 2 screenshots and selecting the correct version, Thanks
Dougie

---

### Post by mojoman on 2007-09-09
It's too slow to be the first one (i.e. Celeron D, Willamette or Northwood). If I'm not mistaken Celeron M is for laptops so if you don't have a laptop I'd scratch that from the list as well. That only leave the third candidate. Now, I also know for a fact that Celeron made 1,3 GHz Tualatin processors so it *could* be that one. If you were taking bets, that's where I'd place my money (and if you have a laptop I might well lose them).

/mojoman

---

### Post by DougieFresh4U on 2007-09-09
> **mojoman said:**
> It's too slow to be the first one (i.e. Celeron D, Willamette or Northwood). If I'm not mistaken Celeron M is for laptops so if you don't have a laptop I'd scratch that from the list as well. That only leave the third candidate. Now, I also know for a fact that Celeron made 1,3 GHz Tualatin processors so it *could* be that one. If you were taking bets, that's where I'd place my money (and if you have a laptop I might well lose them).

/mojoman
Thanks for the advice.
No laptop here:)

---

### Post by nonewmsgs on 2007-09-09
what's the output of 

```

cpuid

```
you might need to sudo apt-get install cpuid

---

### Post by DougieFresh4U on 2007-09-09
> **nonewmsgs said:**
> what's the output of 

```

cpuid

```
you might need to sudo apt-get install cpuid

dougie@DougiesLeanMachine:~$ cpuid
 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
00000001 000006b4 00000001 00000000 0383fbff
00000002 03020101 00000000 00000000 0c040882
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 65746e49 2952286c 6c654320 6e6f7265
80000003 294d5428 55504320 20202020 20202020
80000004 20202020 20202020 30303331 007a484d

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 000006b4:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 11 - 
Stepping 4
Reserved 0

Brand index: 1 [Celeron processor]
Extended brand string: "Intel(R) Celeron(TM) CPU                1300MHz"

Feature flags 0383fbff:
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
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set

TLB and cache info:
01: Instruction TLB: 4KB pages, 4-way set assoc, 32 entries
02: Instruction TLB: 4MB pages, 4-way set assoc, 2 entries
03: Data TLB: 4KB pages, 4-way set assoc, 64 entries
82: 2nd-level cache: 256KB, 8-way set assoc, 32 byte line size
08: 1st-level instruction cache: 16KB, 4-way set assoc, 32 byte line size
04: Data TLB: 4MB pages, 4-way set assoc, 8 entries
0c: 1st-level data cache: 16KB, 4-way set assoc, 32 byte line size

---

### Post by mojoman on 2007-09-09
Tualatin and Coppermine are members of the class Celeron P6 CPUs. I bet Family 6 in your output corresponds to that.
/mojoman

---

### Post by DougieFresh4U on 2007-09-09
> **mojoman said:**
> Tualatin and Coppermine are members of the class Celeron P6 CPUs. I bet Family 6 in your output corresponds to that.
/mojoman

Thanks for info & helping me with my "antique" :)

---

### Post by mojoman on 2007-09-10
Glad it worked. Btw, love the avatar, goes nicely with antique hardware :wink: (though to tell you the truth, two of my three computers are a lot more ancient than yours, and they run just fine)

---

