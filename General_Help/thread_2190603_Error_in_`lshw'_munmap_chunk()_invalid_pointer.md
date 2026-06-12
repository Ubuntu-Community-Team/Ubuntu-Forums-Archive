---
title: "Error in `lshw': munmap_chunk(): invalid pointer"
date: 2013-11-28
forum: General Help
---

### Post by mabinty on 2013-11-28
Dear all,

I have had segfault problems in Ubuntu 13.10 with different applications for a while now. With different kind of difficulties installing 12.04 and 13.10, I finally managed to installed Ubuntu 13.10 a month ago on the following desktop machine:

- ASrock S1150 Z87 Extreme6 motherboard (UEFI BIOS)
- DIMM DDR3 16GB RAM
- Intel S1150 Core i7-4770 CPU (4 cores)
- NVIDIA Quadro K600 graphic card

My main application is the open source CFD tool OpenFOAM, where I use paraview for visualisation. For some days now, the machine behaves in a funny way: after say 30 or 45 min some OpenFOAM applications and/or paraview crash with Aborted/Segmentation fault (core dump) showing memory maps. But also other applications like apt, firefox or thunderbird. Yestarday  even terminal windows or today "sudo lshw" crashed, the latter with

    *** Error in `lshw': munmap_chunk(): invalid pointer: 0x0000000003c114e0 ***
    ======= Backtrace: =========
    /lib/x86_64-linux-gnu/libc.so.6(+0x7f4c6)[0x7f0e095bd4c6]
    lshw[0x44bf6d]
    /lib/x86_64-linux-gnu/libc.so.6(+0x3c071)[0x7f0e0957a071]
    /lib/x86_64-linux-gnu/libc.so.6(+0x3c0f5)[0x7f0e0957a0f5]
    /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xfc)[0x7f0e0955fdec]
    lshw[0x4049c1]
    ======= Memory map: ========
    00400000-004af000 r-xp 00000000 08:01 9962144                          /usr/bin/lshw


Somtimes even the whole machine freezes and I have to do altR+sysReq+REISUB for restart. I could not reproduce this behaviour, it appears to happen randomly, one process triggers the problem and than most other applications crash.

Searching the web brought me to check my RAM with memtest86+. I let the test run 6 passes with no errors except in the first one (see screen shot). But because only one out of 6 passes showed an error I though RAM is ok. Furthermore, I checked the CPU, memory and hard disk with "Disk Utility" and "System Testing" indicating passed tests. 

I really do not know if this is a hardware or software problem.  I attached the output of lspci -v and sudo lshw for some more  info.  Please tell me if its necessary to post parts of the kernel.log and  dmesg or other logs. Hope somebody can give me further hints for troubleshooting.

Thx in advance!!
Aram

PS: For the graphic driver I tried both the open one and the one from NVIDIA 319.32 suggested by Ubuntu. Problems occur with both drivers.

[ATTACH]248154[/ATTACH]

[ATTACH]248155[/ATTACH]

---

### Post by mabinty on 2013-11-28
Forgot to add the output of uname -a:

Linux project 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mabinty on 2013-11-28
It might be worth mentioning that I installed Ubuntu 13.10 by manually partitioning my hard disk using the 'something else' installing option (see attached partition chart). This is different from the "default uefi installation" of 13.10 where I got three partitions, the third one beeing a very small ntfs one. I decided to do a manual partitioning as the "default uefi installation" resulted in an unstable system (which finally I have too now ... ).

Aram

---

### Post by mabinty on 2013-12-04
OK, solved the problem: I changed the broken RAM and now my system runs stable as I was used to in the past :)

What I learned is at the moment memtest86+ shows an error while checking the memory, a defect in the RAM is certain! Whereas if no errors are found, its not certain that the memory is OK, but the probability increases with the number of positive passes.

Cheers,
Aram

---

