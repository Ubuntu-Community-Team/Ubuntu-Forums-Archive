---
title: "Lenovo ThinkPad E440: Ubuntu won't wake up after suspend"
date: 2014-09-24
forum: General Help
---

### Post by Martin_Votruba on 2014-09-24
Hi,
I am running Ubuntu 14 on my Lenovo ThinkPad E440 and each time I suspend the OS I am not able to wake it up - I have to shut it down by long pressing the power button. I have dual boot with Windows 8, there is everything ok, sleep is working just ok. Can you help me, what should I do? Here are some additional informations:

My pastebinit:
[http://paste.ubuntu.com/8415960/](http://paste.ubuntu.com/8415960/)

Information about my video card:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:502a]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)

```

My curren kernel:
```
BOOT_IMAGE=/vmlinuz-3.13.0-36-generic.efi.signed root=UUID=3904817f-9309-4f61-8160-116d16200423 ro quiet splash vt.handoff=7
```

 Thanks!

---

### Post by fadder on 2014-09-27
Hi,

Many of us are having similar problems (I have a thinkpad X220i, Xubuntu 14.04). I haven't found a solution yet, but there are some ideas for workarounds here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1283938]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1283938")

I find the simple suggestion of #10 worked (doing lock-screen, then close the lid). So does typing sudo pm-suspend but typing passwords just to close the lid isn't convenient. 

This problem is a real pain! The older Ubuntus used to deal with suspend perfectly.

---

### Post by henry-gerret on 2014-09-27
This is a really bad problem try turning of your computer then back on and if that dosent work remove hard drive and place it  back

---

