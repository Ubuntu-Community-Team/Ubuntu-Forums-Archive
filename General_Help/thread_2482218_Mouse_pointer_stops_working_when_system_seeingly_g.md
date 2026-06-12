---
title: "Mouse pointer stops working when system seeingly goes into idle mode"
date: 2022-12-24
forum: General Help
---

### Post by wyattwhiteeagle on 2022-12-24
Lubuntu 22.04 (Jammy)

(lscpu posted for info)

What's goin' on is when I let the system go idle, then come back after a time, the mouse pointer doesn't move.

I have the sleep, hybernation, and screensaver turned off and the screen-blanking is disabled.

It started doing this only 3 or 4 days ago.

Has anyone else had this issue?

How might I correct this?

```
wyatt@wyatt-latitudee5400:~$ lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         36 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  2
  On-line CPU(s) list:   0,1
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
    CPU family:          6
    Model:               15
    Thread(s) per core:  1
    Core(s) per socket:  2
    Socket(s):           1
    Stepping:            13
    Frequency boost:     enabled
    CPU max MHz:         2001.0000
    CPU min MHz:         800.0000
    BogoMIPS:            3989.97
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clfl
                         ush dts acpi mmx fxsr sse sse2 ht tm pbe syscall nx lm constant_tsc arch_per
                         fmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx e
                         st tm2 ssse3 cx16 xtpr pdcm lahf_lm pti tpr_shadow vnmi flexpriority vpid dt
                         herm ida
Virtualization features: 
  Virtualization:        VT-x
Caches (sum of all):     
  L1d:                   64 KiB (2 instances)
  L1i:                   64 KiB (2 instances)
  L2:                    2 MiB (1 instance)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0,1
Vulnerabilities:         
  Itlb multihit:         KVM: Mitigation: VMX unsupported
  L1tf:                  Mitigation; PTE Inversion
  Mds:                   Vulnerable: Clear CPU buffers attempted, no microcode; SMT disabled
  Meltdown:              Mitigation; PTI
  Mmio stale data:       Unknown: No mitigations
  Retbleed:              Not affected
  Spec store bypass:     Vulnerable
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:            Mitigation; Retpolines, STIBP disabled, RSB filling, PBRSB-eIBRS Not affecte
                         d
  Srbds:                 Not affected
  Tsx async abort:       Not affected
wyatt@wyatt-latitudee5400:~$ 

```

---

### Post by guiverc on 2022-12-24
I'm unaware of any change that could impact this, but given when it started; I'd likely explore your apt logs to see what changes you downloaded in the session before you noticed the changed for clues (*apt logs are found in /var/log/apt/history.log*)

Your description fits a wireless mouse I use on occasion... Are you using a wireless mouse?

- Check it's batteries

I have another wireless mouse that goes into *power-save* mode on its own when ignored, alas it doesn't wake on movement (*a different brand one does and it's better*), but wakes on my hitting a button.. alas the button is transmitted to the PC which annoys me, so I counter that by using right-click as it has less impact on most applications.

No answers sorry, just my reaction.

---

### Post by wyattwhiteeagle on 2022-12-24
> **guiverc said:**
> I'm unaware of any change that could impact this, but given when it started; I'd likely explore your apt logs to see what changes you downloaded in the session before you noticed the changed for clues (*apt logs are found in /var/log/apt/history.log*)

Your description fits a wireless mouse I use on occasion... Are you using a wireless mouse?

- Check it's batteries

I have another wireless mouse that goes into *power-save* mode on its own when ignored, alas it doesn't wake on movement (*a different brand one does and it's better*), but wakes on my hitting a button.. alas the button is transmitted to the PC which annoys me, so I counter that by using right-click as it has less impact on most applications.

No answers sorry, just my reaction.

Hey, thanks for the quick reply.
Yes, it is a wireless mouse.

I changed the battery last month.
It may be time to change the battery.
It's a cheap battery. (bought at Dollar Tree, i.e. returned to manufacturer then put in a freezer for 24 hours then returned to the consumer shelves as a recycled item)

I will be checking the apt logs.
Meantime, I will try the "right-click trick" to see if that helps.

Thanks for the suggestions.

---

