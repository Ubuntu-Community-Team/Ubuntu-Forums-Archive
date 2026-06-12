---
title: "Nouveau driver freezes"
date: 2021-03-28
forum: General Help
---

### Post by dimitri-papadopoulos on 2021-03-28
Hi,
I have a Dell Precision Tower 3620 with the following graphics and a 3840 × 2160 screen :
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GL [Quadro K1200] (rev a2)
I have been running Ubuntu 16.04, 18.04 and 20.04 on this machine, and with each of these releases it has been freezing from time to time (approximatively once or twice per day). 
```

Feb 26 12:00:15 xxxxxxxx kernel: [15385.625416] nouveau 0000:01:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
Feb 26 12:00:15 xxxxxxxx kernel: [15385.625436] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Feb 26 12:00:15 xxxxxxxx kernel: [15385.625453] nouveau 0000:01:00.0: fifo: channel 6: killed
Feb 26 12:00:15 xxxxxxxx kernel: [15385.625462] nouveau 0000:01:00.0: fifo: engine 5: scheduled for recovery
Feb 26 12:00:15 xxxxxxxx kernel: [15385.625467] nouveau 0000:01:00.0: fifo: engine 0: scheduled for recovery
Feb 26 12:00:15 xxxxxxxx kernel: [15385.626095] nouveau 0000:01:00.0: Xorg[2366]: channel 6 killed!

```

I have opened bug report [#1917037]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1917037"). However, I could use some help to start investigating in more detail. Any suggestions?

Note that switching to proprietary NVidia drivers is currently not an option for me: [NVidia drivers crash on Ubuntu 20.04]("https://ubuntuforums.org/showthread.php?t=2459857&p=14028733").

---

### Post by bcschmerker on 2021-03-28
**One Package in the ubuntu Repositories specific to nVIDIA® GPU's is nouveau-firmware, a needful for Maxwells** (e.g. your GM107GL)**, Pascals, and Voltas; don't know as of 28 March 2021 whether xserver-xorg-video-nouveau has been expanded to Turings and Ampéres.**  The Package xserver-xorg-video-all drags in drivers for pre-Radeon ATi® VDA's, Cirrus Logic® VDA's, Matrox® GPU's, VIA® UniChrome&#8482; VDA's (viz., xserver-xorg-video-openchrome), AMD® RADEON® GPU's, SiS® VDA's, and VESA non-accelerated VDA's in addition to the open-source driver for nVIDIA® GPUs up to Kepler (viz., xserver-xorg-video-nouveau); plus drivers for intel® HD Graphics GPUs and QXL® GPUs under Recommended.

---

### Post by dimitri-papadopoulos on 2021-03-30
I have installed **nouveau-firmware**, hopefully it can help avoid the freeze.

I am unable to understand the **xserver-xorg-video-all** part. This package is not installed, but **xserver-xorg-video-nouveau** is, as well as **xserver-xorg-video-fbdev** and **xserver-xorg-video-vesa**.

---

### Post by dimitri-papadopoulos on 2021-08-03
Unfortunately the nouveau driver keeps freezing.

---

### Post by dimitri-papadopoulos on 2021-08-03
In addition to Ubuntu issue [#1917037]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1917037"), I have opened freedesktop.org issue [#551]("https://gitlab.freedesktop.org/xorg/driver/xf86-video-nouveau/-/issues/551") upstream.

---

### Post by dimitri-papadopoulos on 2021-10-16
An update for the benefit of those reading this post:

I eventually contacted Dell support and was sent a new GM107GL graphics card (under extended warranty). Double improvement:

[LIST]
[*]no more freezing (crossing fingers), 
[*]much less noise from the workstation (although I had cleaned the fan with compressed air). 
[/LIST]
  It looks like the graphics card really had been defective from the start.

---

### Post by dimitri-papadopoulos on 2021-10-21
Unfortunately, I still experience freezes. Perhaps less often - it's hard to tell - but they're still here.

The only positive outcome of the GM107GL graphics card exchange is that the workstation operates silently now.

---

### Post by vmpx on 2021-10-21
**How to fix Ubuntu 18.04 freeze after boot when NVIDIA card installed**

Replace in GRUB menu for 18.04 ”quiet splash” with ”quiet splash  nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.

---

### Post by dimitri-papadopoulos on 2021-10-26
Same freeze again. The interesting thing this time is that the graphic   session recovered on its own. I just had to wait 5 to 10 minutes:


[LIST]
[*]The graphic session freezes while `vlc` is displaying a video.
[*]Sound keeps playing.
[*]Eventually, `vlc` crashes and the graphic session recovers at the exact same time.
[/LIST]

```
nouveau: kernel rejected pushbuf: Aucun périphérique de ce type
nouveau: ch2: krec 0 pushes 1 bufs 12 relocs 0
nouveau: ch2: buf 00000000 00000003 00000004 00000004 00000000
nouveau: ch2: buf 00000001 00000008 00000002 00000002 00000002
nouveau: ch2: buf 00000002 00000006 00000004 00000000 00000004
nouveau: ch2: buf 00000003 0000000a 00000002 00000002 00000002
nouveau: ch2: buf 00000004 00000007 00000002 00000002 00000000
nouveau: ch2: buf 00000005 0000000d 00000002 00000000 00000002
nouveau: ch2: buf 00000006 0000001f 00000004 00000004 00000000
nouveau: ch2: buf 00000007 0000002b 00000004 00000004 00000000
nouveau: ch2: buf 00000008 00000030 00000002 00000002 00000000
nouveau: ch2: buf 00000009 0000000e 00000002 00000000 00000002
nouveau: ch2: buf 0000000a 00000020 00000004 00000004 00000000
nouveau: ch2: buf 0000000b 0000000f 00000002 00000000 00000002
nouveau: ch2: psh 00000000 000002b300 000002bbb4
nouveau:     0x200203fd
nouveau:     0x05000000
nouveau:     0x02d00000
nouveau:     0x20090200
nouveau:     0x00000000
[...]
nouveau:     0x00000000
nouveau:     0x0021c000
nouveau:     0x00013448
nouveau:     0x1000f010
vlc: ../nouveau/pushbuf.c :723 : nouveau_pushbuf_data:  l'assertion « kref » a échoué.

```

---

### Post by dimitri-papadopoulos on 2021-10-26
I will try **nomodeset** as suggested, thank you:

[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)
[https://www.dell.com/support/kbdoc/en-us/000123893/manual-nomodeset-kernel-boot-line-option-for-linux-booting](https://www.dell.com/support/kbdoc/en-us/000123893/manual-nomodeset-kernel-boot-line-option-for-linux-booting)

However, I don't have issues at boot, usually X freezes after a few hours. Will the above help?

---

### Post by dimitri-papadopoulos on 2021-11-03
I haven't tried **nomodeset** yet, because Dell changed the motherboard a week ago. No more freezing after that change, freezing appears to be gone for good. Crossing fingers again &#129310;

Why do you think **nomodeset** could help in this specific case? A quick explanation would help.

---

### Post by dimitri-papadopoulos on 2021-12-17
I can confirm that changing the motherboard fixed this freezing issue - and also another issue where the screen would start flickering (on and off every second or so).

---

### Post by KBar on 2021-12-17
Fantastic. Now, could you please mark the thread as [SOLVED]? Thanks.

---

