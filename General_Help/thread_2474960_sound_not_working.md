---
title: "sound not working"
date: 2022-05-12
forum: General Help
---

### Post by guine on 2022-05-12
I just installed ubuntu 22.04 on a new laptop and I'm not getting sound(the sound worked in windows before installing ubuntu so the hardware is working) from the speakers and if I plug in headphone I hear a light beating sound but thats it. I've tried reloading alsa and trying pulseaudio with no luck. The computer seems to be finding the sound card but when I ran lspci -v | grep -A7 -i "audio" I got this 
```
0000:00:1f.3 Audio device: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20) (prog-if 80)
	Subsystem: ASUSTeK Computer Inc. Tiger Lake-LP Smart Sound Technology Audio Controller
	Flags: bus master, fast devsel, latency 32, IRQ 178, IOMMU group 15
	Memory at 6131288000 (64-bit, non-prefetchable) [size=16K]
	Memory at 6131000000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
```
and I wasn't sure if the capabilities access denied was the problem and if so how to try to fix it or if theres something else that might be wrong.
Thanks

---

### Post by Claus7 on 2022-05-12
Hello,

after upgrading to ubuntu 22.04 I faced some sound problems. One of the things I noticed is that even if the sound bar under sound settings on top panel is to a high level, the sound heard does not match that level. In order to solve this I have to slightly touch the sound level in order to hear normally again.

Another thing I noticed is some low sounds similar to your case, yet from headphones though. The previous solution did not work. What I had to do is to open alsa and manually increase the headphone bar in order to hear sound normally. I suppose, in your case, to experiment and check if some bar/column will solve your problem.

Regards!

---

### Post by #&amp;thj^% on 2022-05-12
This might be a possible: [https://askubuntu.com/questions/1313183/how-do-i-rename-audio-devices-in-ubuntu](https://askubuntu.com/questions/1313183/how-do-i-rename-audio-devices-in-ubuntu)

---

### Post by guine on 2022-05-12
No luck on getting the internal speakers or aux jack to work but I did discover connecting the aux cord through a usb works for both my external speakers and headphones as well as if I plug my external speakers into the computers aux port I get loud constant static.

---

