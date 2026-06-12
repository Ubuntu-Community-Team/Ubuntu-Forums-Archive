---
title: "Kernel panic- not syncing"
date: 2008-05-17
forum: General Help
---

### Post by FlyinRedneck on 2008-05-17
Hello, i am trying to install Ubuntu 8.04 Hardy Heron on a desktop computer with:

AMD Athlon 2000 processor 1.5ghz
1 Gb of ram
On board graphics (I could put my radeon back in)

While i try to boot from the Live CD or the Alternate CD, the main menu appears but if i chose any install option or live option i get this:

I will start about 10 lines before the Kernel Panic

Call Trace:
[<c0217079>] kvaspintf +0x39/0x70
[<c02170c7>] kasprintf+0x17/0x20
[<c04325ae>] kmen _cache_init+0xee/0x190
[<c041b9b5>] start_kernel+0x275/0x3a0
[<c041b130>] unkown_bootoption+0x0/0x1e0
===============================
Code: 15 3c 7e c0 5a 59 89 c6 51 52 ff 15 44 7e 3e c0 5a 59 64 a1 08 f0 46 co 8b 5d 00 85 db 0f 84 8a 00 00 00 8b 45 0c <8b> 04 83 89 45 00 89 f0 51 52 ff 15 40 7e 3e c0 5a 59 66 83 7c
EIP: [<c0189ff4>] __kmalloc=0x64/0x110 SS:ESP 0068:c0417f60
---[ end trace cal43223eefdc828 ]---
Kernel panic - not syncing: Attempted to kill the idle task!


Any help would be greatly appreciated.

---

### Post by insaini on 2008-06-22
Have you solved this problem yet? or anyone know why this is happening..

in my case its a brand new machine

Core 2 Duo 7200
2GB RAM (1066)
250 GB SATA

I havent installed windows or anything its completely fresh.. im trying to install the 64 bit version of Kubuntu 8.04 ... i think im going to try the 32 bit version to see if it installs..

---

