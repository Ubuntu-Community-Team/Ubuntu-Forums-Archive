---
title: "Crackling distortion in all audio output in 16.04 on HP laptop"
date: 2018-04-18
forum: General Help
---

### Post by bookherd on 2018-04-18
For a few weeks now, I've observed audio static (crackly distortion) in all forms of audio/video files played on my laptop, whether through built-in speakers, headphones, or external speakers. The sound worked just fine before that; I don't know what changed or exactly when it happened.

Output of [lspci -v | grep -A7 -i "audio"]:
> 00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at d4730000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])

Things I've tried so far:
- muting microphone
- turning off Bluetooth
- searching forums and elsewhere for clues
I do not have PulseAudio installed.

I don't have a clue how to troubleshoot this, so even your most basic suggestions are appreciated.

---

