---
title: "Ubuntu 18.04 freezes in Dota 2 with sound glitch"
date: 2018-11-14
forum: General Help
---

### Post by a-rogovsky on 2018-11-14
Hi!

This system:
```

inxi -ACDMNSG
System:    Host: OGAGO Kernel: 4.15.0-36-generic x86_64 bits: 64
           Console: tty 1 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Gigabyte product: AB350M-Gaming 3 serial: N/A
           Mobo: Gigabyte model: AB350M-Gaming 3-CF v: x.x serial: N/A
           UEFI: American Megatrends v: F22 date: 03/15/2018
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3000 MHz 1: 1346 MHz 2: 1344 MHz 3: 1346 MHz
           4: 1343 MHz 5: 1342 MHz 6: 1345 MHz 7: 2253 MHz 8: 2257 MHz
           9: 1374 MHz 10: 1374 MHz 11: 1374 MHz 12: 1374 MHz 13: 1374 MHz
           14: 1371 MHz 15: 1374 MHz 16: 1373 MHz
Graphics:  Card: NVIDIA GP104 [GeForce GTX 1070]
           Display Server: X.Org 1.19.6
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 1070/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.48
Audio:     Card Advanced Micro Devices [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-36-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           Card-2: Realtek RTL8192CE PCIe Wireless Network Adapter
           driver: rtl8192ce
Drives:    HDD Total Size: 2750.6GB (36.4% used)
           ID-1: /dev/sda model: Samsung_SSD_860 size: 250.1GB
           ID-2: /dev/sdb model: TOSHIBA_DT01ACA2 size: 2000.4GB
           ID-3: USB /dev/sdc model: External size: 500.1GB

```

When play in Dota 2 or listen music in Youtube (not every time) system begin freezee and repeat last sound fragment (~1 second) every time.
This freezees is absolutley random. Some time system hangs after 5 minutes Youtube or after 3 hours in Dota 2.

Syslog have last log stirng is zero ( hex 0x0).

I dont know what exactly I need search in syslog.

---

### Post by a-rogovsky on 2018-11-20
Any suggestions?

---

