---
title: "[SOLVED] sound off after killing windows"
date: 2007-11-20
forum: General Help
---

### Post by Catalonian on 2007-11-20
Hey, 
I have recently erased windows from one of my hard drives and kept ubuntu.
Before doing so, if I muted the sound on windows and booted ubuntu I couldnt hear anything (it was not muted on ubuntu);  I had to get into windows, unmute, and get back to ubuntu.

Now that I have killed windows, (yes, I killed it while it was on mute :() I have no sound.

It has nothing to do with drivers because I know they work, the sound's just disabled somewhere (maybe the sound card has a mute state programmed by hardware?)

Using lspci -v:

> 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at 54000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Using aplay -l

> card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And everithyng's enabled on alsamixer...

Anyone? :confused:

---

### Post by Catalonian on 2007-11-22
Isn't there any place where I can just enable it (like changing sound from 0 to 1 or whatever :P? Because I know drivers are installed and run very well...I had sound before uninstalling windows...

---

