---
title: "Can't detect headset input"
date: 2020-04-04
forum: General Help
---

### Post by lilspoon0110 on 2020-04-04
Hi I'm having some issues getting my headset properly working on Ubuntu. I recently switched from windows and am still very new to this so please excuse my ignorance. 

Ubuntu detects and plays output just fine, but I can't get any input. In both settings and pavucontrol my headset doesn't show up under input, only output. Only profiles allowed are all output only. I've been trying for awhile and can't seem to find a fix.

I'm using a HyperX Cloud Revolver S but I had to get a replacement sound card. Both linked below:
[HyperX Headset]("https://www.hyperxgaming.com/us/headsets/cloud-revolver-gaming-headset") 
[HyperX Accessories]("https://www.hyperxgaming.com/us/headsets/accessories") (2nd on the list)

The headset has an audio jack coming off of it that plugs into the AMP that I plug into my system through a usb
If I plug in the headset via audio jack I can get it to work as either input or output, but not both bc I have 2 separate jacks.


Here's some information I've gathered up while trying other things

```
spoon@immarobot:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Amp [HyperX Amp], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Amp [HyperX Amp], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```



```
spoon@immarobot:~$ amixer -c0
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 44 [69%] [-20.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',16
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 28 [61%] [12.00dB] [on]
  Front Right: Capture 28 [61%] [12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
```


```
spoon@immarobot:~$ inxi -Fxz
System:    Host: immarobot Kernel: 5.3.0-45-generic x86_64
           bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: H170-PRO v: Rev X.0x serial: N/A
           UEFI [Legacy]: American Megatrends v: 1803 date: 05/06/2016
CPU:       Quad core Intel Core i7-6700 (-MT-MCP-) 
           arch: Skylake-S rev.3 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27199
           clock speeds: max: 4000 MHz 1: 1136 MHz 2: 2856 MHz 3: 3182 MHz
           4: 3453 MHz 5: 3399 MHz 6: 3374 MHz 7: 3318 MHz 8: 3431 MHz
Graphics:  Card-1: Intel HD Graphics 530 bus-ID: 00:02.0
           Card-2: NVIDIA GP106 [GeForce GTX 1060 3GB] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.5 )
           drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 1060 3GB/PCIe/SSE2
           version: 4.6.0 NVIDIA 435.21 Direct Render: Yes
Audio:     Card-1 Intel 100 Series/C230 Series Family HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1f.3
           Card-2 NVIDIA GP106 High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-3 Kingston driver: USB Audio usb-ID: 001-006
           Sound: Advanced Linux Sound Architecture v: k5.3.0-45-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 port: d000 bus-ID: 04:00.0
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1120.2GB (7.3% used)
           ID-1: /dev/sda model: ADATA_SP550 size: 120.0GB
           ID-2: /dev/sdb model: WDC_WD10EZEX size: 1000.2GB
Partition: ID-1: / size: 108G used: 39G (38%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 704M used: 190M (30%) fs: ext4 dev: /dev/sda1
           ID-3: /home size: 916G used: 37G (5%) fs: ext4 dev: /dev/sdb1
           ID-4: swap-1 size: 1.03GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.0C mobo: N/A gpu: 0.0:42C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 328 Uptime: 31 min Memory: 2750.4/15873.6MB
           Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 
```


Like I said I'm a noob so sorry if I provided too much/little detail or misused anything in this post.
If anyone could help me out it would be much appriciated, thank you!!

---

### Post by TheFu on 2020-04-04
In pavcontrol, the far right tab, verify that the headset device is set to "duplex", then work from right to left in the other tabs.
i usually disable any devices that won't be used (set them off) to prevent different programs from getting confused.

Pulse tries to connect the latest device up, so sometimes after doing all of that, i'll unplug then re-plug the headset back in. That always fixes it provided i've disabled other devices already.

---

### Post by lilspoon0110 on 2020-04-05
You're talking about the "Profile" under the "Configuration" tab right? If so, I don't have a duplex option, only 3 different outputs, "Analog Stereo", "Digital Stereo", and "Analog Surround 1.7"

---

### Post by owbizi on 2020-04-06
Are you by chance using pulseaudio (default)? You can check if it is running by executing on your terminal:

> 
ps aux | grep -i pulseaudio


If the answer is positive, I had a similar issue in my machine. Try adding the following line to the file **/etc/pulse/default.pa**:

> 
load-module module-alsa-source device=hw:1,0


The above must be added **before** the line **.ifexists module-udev-detect.so**.

I'm running pulseaudio as per-user mode over here, but if you're running it as a system service, then the correct file would be **/etc/pulse/system.pa**.

In some cases, you may also have it in your user directory in **~/.config/pulse/default.pa**. Worth checking it out first.

Reboot and check if the input is now detected in pavucontrol. Otherwise, you may also try with **device=hw:1,1**.

---

### Post by TheFu on 2020-04-06
Setting up specific config files for specific devices seems like a bad idea, as pulse will always try to make the last connected device get priority.  Devices that are plugged and unplugged will connect to different HW channels, so those will always change.

A headset should have a "duplex" mode, since the mic would be input and the speakers would be output.  The only reason that wouldn't be the situation is if a special driver is needed for the headset to work and that driver is missing.  I've not need that issue with my USB headsets. They were always just plug-n-play .... with a little pavcontrol tweaking.

---

### Post by lilspoon0110 on 2020-04-06
I am in default mode, but adding the line broke pavucontrol and made my pc not detect any sound cards. Also tried turning off Fast Boot but that didn't do anything for me either.

---

### Post by lilspoon0110 on 2020-04-06
@TheFu That's pretty much what I was expecting but it doesn't want to seem to work for me. Only sees my headset as speakers for some reason. No such thing as duplex mode for some reason. You would change that under the "Configuration" tab in pavucontrol right?

---

### Post by TheFu on 2020-04-06
Don't forget to check the output levels and input levels on the other tabs.  Also, there a difficult-to-understand button/icon that does mute the input or output for a specific channel.  Check those.

pavcontrol is a complex app that looks simple.  The GUi team around it had to solve not just our trivial needs but those for much more complex setups which I&#8217;ll never use.  Some DEs have a simplified Sound Controller app included.  Check if your system has one of those.  i don't use any DE, so I&#8217;m stuck w/ pavcontrol or pacmd.

---

### Post by lilspoon0110 on 2020-04-06
@TheFu Yeah I also have the Sound section in the system settings. None of these applications are detecting any sort of input from my headset and doesn't give me any input profiles to change to. Nothing is muted unless there is something that is going completely over my head. I don't see any mute options in System Sound and pavucontrol only had had options to mute output

---

### Post by TheFu on 2020-04-06
Sorry, all my headsets and microphones are plug-n-play.  They are all USB connected, if that helps.  The 2.5mm mics never worked well for me.

---

### Post by lilspoon0110 on 2020-04-06
No worries, thanks anyways. Yeah that's kinda what I was expecting.. It works through the 2.5mm but not the USB lol

---

### Post by TheFu on 2020-04-06
> **lilspoon0110 said:**
> No worries, thanks anyways. Yeah that's kinda what I was expecting.. It works through the 2.5mm but not the USB lol

Are you certain the USB isn't for the speakers only and the 2.5mm for the microphone?  I’ve seen that over the yrs.

---

