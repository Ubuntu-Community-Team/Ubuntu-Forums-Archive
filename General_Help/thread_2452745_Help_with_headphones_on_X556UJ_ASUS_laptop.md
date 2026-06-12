---
title: "Help with headphones on X556UJ ASUS laptop"
date: 2020-10-27
forum: General Help
---

### Post by cppurist on 2020-10-27
[SIZE=4]Hello,

I'll get right to the problem: I have an ASUS laptop, model X556UJ on which I've installed Ubuntu 20.04.1 LTS. One of my teachers said that he couldn't hear me because the laptops internal mic had a low quality.

So I bought a pair of headphones with a microphone and tried using HDAJackRetask (from the alsa-tools-gui package) to override the pins in order for the headphones to work. Also I've tried modifying the /etc/modprobe.d/alsa-base.conf frile from my computer.

I don't know how I've messed up the pins or the file, but unfortunately the next strange situation appeared: the speakers work properly (laptop+headphones) and the mics work really strange: in the settings of the OS I can clearly see the mic picking up something but other apps, like Firefox, don't actually record anything.

I would prefer a solution that makes everything work properly, but I'd definitelly take a solution that allows me to have the mic from the headphones and the laptop's speakers working simultaneaslly. 

I'll attach to this post all of the information I think is relevant to solving the problem at hand: the codec for the sound-board, the audio devices obtained with the lpsci -v command, photographic evidence of the strange behaviour.

Codec: Realtek ALC255

Audio-devices:

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 130
    Memory at df328000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at df080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

Thank you in advance for your support.
[/SIZE]

---

