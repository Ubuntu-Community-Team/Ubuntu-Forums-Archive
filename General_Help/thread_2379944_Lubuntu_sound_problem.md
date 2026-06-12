---
title: "Lubuntu sound problem"
date: 2017-12-11
forum: General Help
---

### Post by cruzer001 on 2017-12-11
I have encountered an odd problem with sound after installing Lubuntu on this old laptop.  Sound will not work on bootup or reboot, however if I first bring up Mplayer it will work every time.  So first thought was I simply needed to reset sound after system boot.  Using the commands ```
[FONT=arial black]pulseaudio -k && sudo alsa force-reload[/FONT] or [FONT=Arial Black]killall pulseaudio[/FONT] and pulseaudio
``` do nothing.  So I wonder what magic Mplayer is doing.  Any thoughts?

```
inxi -bA
System:    Host: lu1 Kernel: 4.4.0-103-generic i686 (32 bit) Desktop: LXDE (Openbox 3.6.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Sony (portable) product: VGN-FS840 v: C3LLTARA
           Mobo: N/A model: N/A Bios: Phoenix v: R0094J1 date: 06/02/2006
CPU:       Single core Intel Pentium M (-UP-) speed: 1733 MHz (max)
Graphics:  Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) Resolution: 1280x800@59.97hz
           GLX Renderer: Mesa DRI Intel 915GM x86/MMX/SSE2 GLX Version: 1.4 Mesa 17.0.7
Audio:     Card Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-103-generic
Network:   Card-1: Intel PRO/Wireless 2200BG [Calexico2] Network Connection driver: ipw2200
           Card-2: Intel 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile driver: e100
Drives:    HDD Total Size: 100.0GB (6.6% used)
Info:      Processes: 129 Uptime: 1:35 Memory: 760.0/2004.8MB Client: Shell (bash) inxi: 2.2.35
```

Thanks for reading

---

### Post by Yellow Pasque on 2017-12-11
Get alsa info right after you boot. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Then run it again after you run mplayer and have sound working.

---

### Post by cruzer001 on 2017-12-11
Excellent idea; will get on this in a while.  Thanks :)

---

### Post by forneus2 on 2017-12-12
My problem is sound disappeared all over the system. I accidentally hit the mute key when adjusting sound during video playback on mplayer - and the sound was gone. Tried reboot, tried alsa force restart, tried the commands you posted above - no result. :((

---

### Post by cruzer001 on 2017-12-14
> **Temüjin said:**
> Get alsa info right after you boot. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Then run it again after you run mplayer and have sound working.

Sorry for the delay, this got pushed to the back burner :)  

Anyhow both reports (using the ***diff*** command) are identical.  So I just used an easy fix and added Gplayer to my startup programs.

I'm calling this fixed with a work-a-round.

Thanks ):P

---

