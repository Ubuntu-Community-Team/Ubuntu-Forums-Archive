---
title: "Popping Sound on HDMI with S/PDIF on Youtube, Ubuntu 14.04 LTS"
date: 2016-01-20
forum: General Help
---

### Post by chip256 on 2016-01-20
I also posted this on the Ubuntu launchpad site.  
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/281252](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/281252)

Running Ubuntu 14.04 LTS 64-bit
 I am trying to get sound out of my ATI Radeon RV770 (HD 4890).  After about 40 seconds into a video the audio pops and cracks.


 Muting and unmuting restores clear sound temporary.  Restarting the stream also restores clear sound temporary.

EDIT: This also occurs with local video and stereo or 5.1 surround.


 I have tried the solution posted here <<[http://askubuntu.com/questions/405071/static-and-crackling-in-my-hdmi-audio](http://askubuntu.com/questions/405071/static-and-crackling-in-my-hdmi-audio)>> but the situation did not improve.  I have also tried other posted solutions but did not save the web pages.


 05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV790 [Radeon HD 4890] (prog-if 00 [VGA controller])
 Subsystem: XFX Pine Group Inc. Device 2700
 Flags: bus master, fast devsel, latency 0, IRQ 29
 Memory at d0000000 (64-bit, prefetchable) [size=256M]
 Memory at fe2e0000 (64-bit, non-prefetchable) [size=64K]
 I/O ports at 6c00 [size=256]
 [virtual] Expansion ROM at fe200000 [disabled] [size=128K]
 Capabilities: [50] Power Management version 3
 Capabilities: [58] Express Legacy Endpoint, MSI 00
 Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
 Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
 Kernel driver in use: radeon
 05:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
 Subsystem: XFX Pine Group Inc. Device aa30
 Flags: bus master, fast devsel, latency 0, IRQ 28
 Memory at fe2fc000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: [50] Power Management version 3
 Capabilities: [58] Express Legacy Endpoint, MSI 00
 Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
 Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
 Kernel driver in use: snd_hda_intel

---

