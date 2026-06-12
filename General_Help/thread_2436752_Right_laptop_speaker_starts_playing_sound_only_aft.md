---
title: "Right laptop speaker starts playing sound only after the left one"
date: 2020-02-12
forum: General Help
---

### Post by rendoir on 2020-02-12
Occasionally, when playing a sound my right speaker takes a second or less to start playing that sound while the left one starts right away. They are in synch but it's noticeable when the the right one "kicks in".


I'm running a fresh install of Ubuntu 18.04.4 (checked the third-party driver option) in my MSI GE72 2QL Apache laptop.


Running `lspci -v` gives me 2 audio devices:


```
    00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 0a)
	    Subsystem: Micro-Star International Co., Ltd. [MSI] Broadwell-U Audio Controller
	    Flags: bus master, fast devsel, latency 0, IRQ 34
	    Memory at a3314000 (64-bit, non-prefetchable) [size=16K]
	    Capabilities: <access denied>
	    Kernel driver in use: snd_hda_intel
	    Kernel modules: snd_hda_intel


    00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
	    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset High Definition Audio Controller
	    Flags: bus master, fast devsel, latency 0, IRQ 31
	    Memory at a3310000 (64-bit, non-prefetchable) [size=16K]
	    Capabilities: <access denied>
	    Kernel driver in use: snd_hda_intel
	    Kernel modules: snd_hda_intel

```

---

