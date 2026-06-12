---
title: "No sound in Firefox Video's 16.04 distro"
date: 2016-07-16
forum: General Help
---

### Post by Bob_Pennington on 2016-07-16
I've installed Lubuntu 16.04 (Kernel 4.2.0.28) on my laptop (Lenovo G50-45).  Initial install did not detect wireless, etc.; so researching problem found my wireless card was only supported in kernel 4.3 and beyound.  I should say that at this point; sound worked in all places (VLC, Firefox, etc.). Upgraded distro to Kernel 4.6.  Wireless works now and sound is good in VLC (have to set audio to Generic HD default, ???); but no sound in Firefox video's or Audacious.  Note:  VLC in kernel 4.2 showed devices "HDMI HD" & "Generic HD Anolog"; with VLC on 4.6 only Generic Analog is shown...??
Here's the output concerning multimedia on 4.6:

blp@Lenovo-G50-45:~$ sudo lshw -C "multimedia"
  *-multimedia:0          
       description: Audio device
       product: Kabini HDMI/DP Audio
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:43 memory:f0d60000-f0d63fff
  *-usb:0
       description: Video
       product: Lenovo EasyCamera
       vendor: Azurewave
       physical id: 2
       bus info: usb@4:1.2
       version: 1.22
       serial: NULL
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia:1
       description: Audio device
       product: FCH Azalia Controller
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:44 memory:f0d64000-f0d67fff

Any help or info is greatly appreciated.  Thanks in advance.

---

### Post by TheFu on 2016-07-17
On my system with 16.04, pulse audio daemon dies constantly. Don't know why, but restarting it fixes the sound ... until it dies again.
```
pulseaudio -k # kill a daemon
pulseaudio -D # restart the pulse daemon

```
Oh how I hate pulse, just haven't gotten around to purging it and setting up alsa (which is more manual).

---

### Post by Bob_Pennington on 2016-07-18
Solved by going back to lubuntu 15.10 and upgrading kernel to 4.4.5.  After applying launchpad bug 1436940 fix for my laptop wireless and setting up ALSA for Generic HD Analog Output, all works great.
Note:  Thanks for the suggestion TheFu, but pulseaudio is not used in either version 15.10 or 16.04 in Lubuntu.

---

### Post by Geoffrey_Arndt on 2016-07-18
Just be aware 15.10 support ends by Aug 1 or so.

---

