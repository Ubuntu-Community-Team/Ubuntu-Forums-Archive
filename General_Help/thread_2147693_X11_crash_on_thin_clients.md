---
title: "X11 crash on thin clients"
date: 2013-05-22
forum: General Help
---

### Post by lykwydchykyn on 2013-05-22
I'm running LTSP on Ubuntu 12.04.  My clients keep having X11 crashes at random moments which leave them at a black screen.

I grabbed an Xorg log from one of the crashed clients and here are the log entries from the time of the crash (previous log entries are from hours before, probably irrelevant):

```

[ 54253.740] (II) evdev: Power Button: Close
[ 54253.740] (II) UnloadModule: "evdev"
[ 54253.740] (II) Unloading evdev
[ 54253.772] (II) evdev: Power Button: Close
[ 54253.772] (II) UnloadModule: "evdev"
[ 54253.772] (II) Unloading evdev
[ 54253.773] (II) evdev: USB Optical Mouse: Close
[ 54253.773] (II) UnloadModule: "evdev"
[ 54253.773] (II) Unloading evdev
[ 54253.776] (II) evdev: DELL DELL USB Keyboard: Close
[ 54253.776] (II) UnloadModule: "evdev"
[ 54253.776] (II) Unloading evdev
[ 54254.102] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[ 54254.102] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[ 54254.103] 
Fatal server error:
[ 54254.103] xf86CloseConsole: VT_ACTIVATE failed: Input/output error
[ 54254.103] 
[ 54254.103] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[ 54254.103] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[ 54254.103] 
[ 54254.103] 
Backtrace:
[ 54254.103] 0: X (xorg_backtrace+0x37) [0x9337a7]
[ 54254.103] 1: X (0x7ab000+0x18c52a) [0x93752a]
[ 54254.103] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x16c40c]
[ 54254.103] 3: X (0x7ab000+0x192c54) [0x93dc54]
[ 54254.103] 4: X (CloseWellKnownConnections+0x34) [0x934604]
[ 54254.104] 5: X (0x7ab000+0x1944a9) [0x93f4a9]
[ 54254.104] 6: X (0x7ab000+0x19451f) [0x93f51f]
[ 54254.104] 7: X (0x7ab000+0x194615) [0x93f615]
[ 54254.104] 8: X (0x7ab000+0x9d465) [0x848465]
[ 54254.104] 9: X (xf86CloseConsole+0x162) [0x848e12]
[ 54254.104] 10: X (ddxSigGiveUp+0xad) [0x8260fd]
[ 54254.104] 11: X (ddxGiveUp+0x23) [0x826133]
[ 54254.104] 12: X (0x7ab000+0x255bf) [0x7d05bf]
[ 54254.104] 13: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0x33b4d3]
[ 54254.104] 14: X (0x7ab000+0x25699) [0x7d0699]
[ 54254.104] Segmentation fault at address 0x44
[ 54254.104] 
Caught signal 11 (Segmentation fault). Server aborting

```

Hardware on the client is:
```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2)
03:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

any help is appreciated.
Thanks.

---

### Post by lykwydchykyn on 2013-05-28
bump.  Any help appreciate, thanks.

---

