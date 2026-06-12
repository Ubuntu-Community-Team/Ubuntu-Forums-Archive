---
title: "Ubuntu doesn't recognize all my ram ( 1.7GB out of 4GB), what can I do to fix?"
date: 2014-04-27
forum: General Help
---

### Post by dujiexi on 2014-04-27
Hello, I need your help! I have read many thread like this problem, but I still can't solve it. I don't think it's a hardware problem, or my graphic chip share some of my ram, because when I ran windows 8 it worked well with 4GB ram, and my intel graphic chip can't take that much ram, am I right? My BIOS can recognize all of it, and I have updated the BIOS recently.

here are some check by myself  may help:

1. run uname -a ( I used trusty stock kernel before, and I was told to update the kernel to solve it, but it doesn't help)
```
due2me@ThinkPad:~$ uname -a
Linux ThinkPad 3.15.0-031500rc2-generic #201404201435 SMP Sun Apr 20 18:36:18 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

2.run free -m
```
due2me@ThinkPad:~$ sudo free -m[sudo] password for due2me: 
             total       used       free     shared    buffers     cached
Mem:          1698       1516        181        293         18        687
-/+ buffers/cache:        810        888
Swap:         3431        261       3170

```

3.run dmidecode -t 17
```
Handle 0x000C, DMI type 17, 34 bytesMemory Device
    Array Handle: 0x000B
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Hynix/Hyundai
    Serial Number: 00000000
    Asset Tag: None
    Part Number: HMT325S6DFR6C-H9  
    Rank: Unknown
    Configured Clock Speed: 1333 MHz

```

4.run check-my-memory.py
```
check-my-memory.py - version: SJ 2014-03-16OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 1 memory module(s)
BIOS offers 1805 MB as usable
Memory seen by OS 1698 MB
BIOS version 02/07/2014
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit


SUMMARY:
Memory difference between DIMM hardware and BIOS offering 2291 MB
Memory difference between BIOS offering and memory seen by OS 107 MB
Memory difference between DIMM hardware and memory seen by OS 2398 MB


ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory


Finally: show more detailed memory info from lshw and dmidecode. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          size: 4GiB
       description: BIOS
       size: 128KiB
       capacity: 11MiB
BIOS Information
    Vendor: LENOVO
    Version: GDETA5WW (1.65 )
    Release Date: 02/07/2014
--
System Information
    Manufacturer: LENOVO
    Product Name: 33473XC
    Version: ThinkPad Twist




    Maximum Capacity: 8 GB


Finished

```

---

### Post by oldfred on 2014-04-27
I do not know why Windows 8 would see more RAM than BIOS reports.

I might just try booting with each memory chip separately to see if both are really working. And to see which one may be the problem.

Sometimes just reseating memory or cleaning and reseating memory helps.

---

