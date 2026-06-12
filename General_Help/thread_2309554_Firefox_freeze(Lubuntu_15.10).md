---
title: "Firefox freeze(Lubuntu 15.10)"
date: 2016-01-11
forum: General Help
---

### Post by bojan2 on 2016-01-11
Since i installed lubuntu firefox freezes at random. I noticed that it freezes the most when i open Open Menu -> Open Help Menu , but freeze is still random.
Mouse is responding but i can't use it to close firefox. After some time mouse freezes too. Also Ctrl+Alt+F1 does not work. Only solution is reset.
I successfully replicated freeze for three times and found this four lines in syslog at time of the freezes.

```

Jan 11 20:24:56 bojan kernel: [  888.328147] NVRM: GPU at PCI:0000:02:00: GPU-48ef9c66-4339-41dd-0635-3e3803289594
Jan 11 20:24:56 bojan kernel: [  888.328156] NVRM: Xid (PCI:0000:02:00): 8, Channel 00000001
Jan 11 20:24:58 bojan kernel: [  890.328070] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jan 11 20:25:00 bojan kernel: [  892.328454] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context

```

As far as i know this NVRM thing is somehow related to nvidia. 
My graphics card is GeForce GT 220.
I am using 340.96 drivers installed from additional drivers menu.
So far i didn't have any problems related with freezing. Firefox is only problem.
How to solve this problem without reverting to nouveau.

---

### Post by QDR06VV9 on 2016-01-11
[COLOR=#333333][FONT=Helvetica Neue]Well, this is probably an issue on nvidia side then. Try reporting to them (use their forums unless you find a better way).
Plenty of post's here [/FONT][/COLOR][https://devtalk.nvidia.com/default/topic/903841/nvrm-os_schedule-attempted-to-yield-the-cpu-while-in-atomic-or-interrupt-context-/](https://devtalk.nvidia.com/default/topic/903841/nvrm-os_schedule-attempted-to-yield-the-cpu-while-in-atomic-or-interrupt-context-/)
[COLOR=#333333][FONT=Helvetica Neue]The driver 352.63 seems to have the least hicup's at least for me..
[/FONT][/COLOR]```
inxi -G
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63

```[COLOR=#333333][FONT=Helvetica Neue]
I'm not saying that driver will fix your problem but worth a try if nothing better comes up.
Kind Regards

[/FONT][/COLOR]

---

### Post by bojan2 on 2016-01-12
> **runrickus said:**
> [COLOR=#333333][FONT=Helvetica Neue]Well, this is probably an issue on nvidia side then. Try reporting to them (use their forums unless you find a better way).
Plenty of post's here [/FONT][/COLOR][https://devtalk.nvidia.com/default/topic/903841/nvrm-os_schedule-attempted-to-yield-the-cpu-while-in-atomic-or-interrupt-context-/](https://devtalk.nvidia.com/default/topic/903841/nvrm-os_schedule-attempted-to-yield-the-cpu-while-in-atomic-or-interrupt-context-/)
[COLOR=#333333][FONT=Helvetica Neue]The driver 352.63 seems to have the least hicup's at least for me..
[/FONT][/COLOR]```
inxi -G
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63

```[COLOR=#333333][FONT=Helvetica Neue]
I'm not saying that driver will fix your problem but worth a try if nothing better comes up.
Kind Regards

[/FONT][/COLOR]


Well for my card latest driver is 340.96, but i will try with reporting this to nvidia.

---

