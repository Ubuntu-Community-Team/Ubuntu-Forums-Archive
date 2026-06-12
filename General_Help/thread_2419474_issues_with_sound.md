---
title: "issues with sound"
date: 2019-05-22
forum: General Help
---

### Post by christon74 on 2019-05-22
Good evening fellow Ubunters_:smile: It started yesterday. Whichever I try to use, VLC or Rhythmbox, the sound "breaks" on and off. Hardware is a Fujitsu-Siemens Esprimo  E5731- E stars with  7 Gb RAM. Inside a terminal window I have typed: 
find /lib/modules/`uname -r` | grep snd
And the result is a massive list of sound files all ending in "ko". This is perhaps an indication I have installed conflicting audio packages?

sudo aplay -l gives this:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
	Subsystem: Fujitsu Technology Solutions 82801JD/DO (ICH10 Family) HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at fc520000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

Thanks in advance for all help, and friendly greetings from the blue banana region):P.

---

