---
title: "Audio device detection doesnt work properly"
date: 2022-02-10
forum: General Help
---

### Post by witherspoon2 on 2022-02-10
Hi everbody, 

I have installed Ubuntu 20.04 on a Kuu-Laptop and have issues with the onboard speakers (no sound) and the headphone jack (not detected). After the initial installation the only audio output-device was "Dummy Output". After adding these lines to /etc/modprobe.d/alsa-base.conf and a restart, the output-device changed to "HDMI / DisplayPort - Eingebautes Tongerät" (Builtin Audio Device):
```
options snd-hda-intel model=generic
options snd-hda-intel dmic_detect=0
```
Still no sound from the onboard speakers and headphone jacks are not displayed as an output device. Bluetooth headphones however do work fine. 

A few details from the console:
uname 
```
Linux bettina-A8S-PRO 5.13.0-28-generic #31~20.04.1-Ubuntu SMP Wed Jan 19 14:08:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```
aplay -l
```
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: PCH [HDA Intel PCH], Gerät 3: Generic Digital [Generic Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #
```

aplay -L
```
default
    Playback/recording through the PulseAudio sound server
surround21
    2.1 Surround output to Front and Subwoofer speakers
surround40
    4.0 Surround output to Front and Rear speakers
surround41
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50
    5.0 Surround output to Front, Center and Rear speakers
surround51
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, Generic Digital
    HDMI Audio Output
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Hardware device with all software conversions
usbstream:CARD=PCH
    HDA Intel PCH
    USB Stream Output
```

Opening AlsaMixer for HDA Intel PCH doesnt give me a volume-bar to regulate.

Any hints and ideas are wellcome. :-)

---

### Post by MAFoElffen on 2022-02-11
The Linux utility 'lswh' may not be installed by default on your system, but might be helpful to try to diagnose what is going on here...

If the output from this is blank...
```

which lshw

```
then 
```

sudo apt install -y lshw

```
Once there, then 
```

sudo lshw -c multimedia

```
Please post the results of that, wrapped within CODE TAGs. If you do not know what code tags are, just ask first...

That output should show us what hardware chipsets your system is using for it's audio and if it is using any audio driver for it. If not presently using a driver, it would give us an idea of what audio driver you should be using...

---

### Post by witherspoon2 on 2022-02-11
Thank you for the quick reply. Here is what I got:

```
sudo lshw -c multimedia
*-multimedia              
       Beschreibung: Multimedia audio controller
       Produkt: Intel Corporation
       Hersteller: Intel Corporation
       Physische ID: e
       Bus-Informationen: pci@0000:00:0e.0
       Version: 06
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list
       Konfiguration: driver=snd_hda_intel latency=0
       Ressourcen: irq:25 memory:a1210000-a1213fff memory:a1000000-a10fffff
  *-usb:2
       Beschreibung: Video
       Produkt: SHUNCCM2MP
       Hersteller: Alcor Micro, Corp.
       Physische ID: 6
       Bus-Informationen: usb@1:6
       Version: 18.10
       Fähigkeiten: usb-2.00
       Konfiguration: driver=uvcvideo maxpower=200mA speed=480Mbit/s
```

---

### Post by #&amp;thj^% on 2022-02-11
would you also show this:
```
hwinfo --sound
```
installed with:
```
sudo apt install hwinfo
```
it's on the same lines as MAFoElffen suggested, but shows a little more, like state of driver.
Example:
```
$ hwinfo --sound
09: PCI 04.0: 0403 Audio device                                 
  [Created at pci.386]
  Unique ID: 8otl.dUB9I7pKfkE
  SysFS ID: /devices/pci0000:00/0000:00:04.0
  SysFS BusID: 0000:00:04.0
  Hardware Class: sound
  Model: "Red Hat QEMU Virtual Machine"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2668 "82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
  SubVendor: pci 0x1af4 "Red Hat, Inc."
  SubDevice: pci 0x1100 "QEMU Virtual Machine"
  Revision: 0x01
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfc050000-0xfc053fff (rw,non-prefetchable)
  IRQ: 26 (1502 events)
  Module Alias: "pci:v00008086d00002668sv00001AF4sd00001100bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
I have seen lots of complaints/issues with sound with your machine in other forums.

---

### Post by witherspoon2 on 2022-02-11
Here is the output:

```
sudo hwinfo --sound
28: PCI 0e.0: 0401 Multimedia audio controller                  
  [Created at pci.386]
  Unique ID: vuMS.TteBdSHq9c1
  SysFS ID: /devices/pci0000:00/0000:00:0e.0
  SysFS BusID: 0000:00:0e.0
  Hardware Class: sound
  Device Name: "Onboard - Sound"
  Model: "Intel Multimedia audio controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3198 
  SubVendor: pci 0x2782 
  SubDevice: pci 0x0204 
  Revision: 0x06
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xa1210000-0xa1213fff (rw,non-prefetchable)
  Memory Range: 0xa1000000-0xa10fffff (rw,non-prefetchable)
  IRQ: 25 (1 event)
  Module Alias: "pci:v00008086d00003198sv00002782sd00000204bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Driver Info #1:
    Driver Status: snd_soc_skl is active
    Driver Activation Cmd: "modprobe snd_soc_skl"
  Driver Info #2:
    Driver Status: snd_sof_pci_intel_apl is active
    Driver Activation Cmd: "modprobe snd_sof_pci_intel_apl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

### Post by #&amp;thj^% on 2022-02-11
That's better than I hoped, now this is kind of by the seat of my pants here, 
Have good back-ups in place first, before proceeding.
Try the following commands.
```

echo "options snd-hda-intel dmic_detect=0" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

Now, reload alsa and reboot. (Run one line at a time)
```

sudo killall pulseaudio
sudo alsa force-reload
sudo reboot
```
I'm at work right now so I'll have to check back with you in while.
Good Luck

---

### Post by witherspoon2 on 2022-02-11
Thank you for the idea 1fallen, that is a common fix. As part of it, I had already added these two lines to the alsa-base.conf:
```
options snd-hda-intel model=generic
options snd-hda-intel dmic_detect=0
``` 
I still tried it, but adding the last line a second time (and reloading alsa and reloading pulse and rebooting) didnt change the situation. Therefore I have now undone it (removing this one line and doing the reloading part again).

One more information: if one of these two lines is missing it shows only the "Dummy Output".

---

### Post by #&amp;thj^% on 2022-02-11
> **witherspoon2 said:**
> Thank you for the idea 1fallen, that is a common fix. As part of it, I had already added these two lines to the alsa-base.conf:

One more information: if one of these two lines is missing it shows only the "Dummy Output".

Yes you did, I missed that part, show me this please:
```
apt policy timidity-daemon
```
While we're at this one as well:
```
systemctl --failed
```

---

### Post by witherspoon2 on 2022-02-11
Here you go. The second line translates as "installed: (none).
```
apt policy timidity-daemon
timidity-daemon:
  Installiert:           (keine)
  Installationskandidat: 2.14.0-8build1
  Versionstabelle:
     2.14.0-8build1 500
        500 http://de.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu focal/universe i386 Packages
```

And here:
```
systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION
0 loaded units listed.
```

Running both with and without sudo shows the same result.

---

### Post by #&amp;thj^% on 2022-02-11
Thanks, I'm going to talk with a friend but I'll need this:
```
inxi -AC --no-host

```
Mine:
```
inxi -AC --no-host
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1399 min/max: 1400/3000 cores: 1: 1397 2: 1397 3: 1397
    4: 1398 5: 1416 6: 1397 7: 1397 8: 1408 9: 1397 10: 1397 11: 1397 12: 1397
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor driver: N/A
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound Server-1: ALSA v: k5.15.21-hardened1-1-hardened running: yes
  Sound Server-2: PipeWire v: 0.3.45 running: yes


```
Lets for-go using sudo for a while.

---

### Post by witherspoon2 on 2022-02-11
Thank you for your efforts. 

```
inxi -AC --no-host
CPU:       Topology: Quad Core model: Intel Celeron J4125 bits: 64 type: MCP L2 cache: 4096 KiB 
           Speed: 1086 MHz min/max: 800/2700 MHz Core speeds (MHz): 1: 1022 2: 1164 3: 1090 
           4: 962 
Audio:     Device-1: Intel driver: snd_hda_intel 
           Sound Server: ALSA v: k5.13.0-28-generic 
```

---

### Post by #&amp;thj^% on 2022-02-11
> **witherspoon2 said:**
> Thank you for your efforts. 

```
inxi -AC --no-host
Audio:     Device-1: Intel driver: snd_hda_intel 
           Sound Server: ALSA v: k5.13.0-28-generic 
```
Your very Welcome.
That is troublesome,  shows nothing running.
EG:
```
Sound Server-1: ALSA v: k5.15.21-hardened1-1-hardened[COLOR="#FF0000"] running: yes[/COLOR]
  Sound Server-2: PipeWire v: 0.3.45[COLOR="#FF0000"] running: yes[/COLOR]

```
Be Back when I can with or without good news.
**EDIT: BTW please be sure your running up to date Bios and Firmware.**
I will be hung by the neck :) if don't include this as well: (Just shows logs)
```
journalctl -k | grep -Ei "ALSA|HDA|sof|HDMI|snd[_-]|sound|hda.codec|hda.intel"
```

---

### Post by witherspoon2 on 2022-02-11
Well I havent done a bios or firmware-update yet. 

```
journalctl -k | grep -Ei "ALSA|HDA|sof|HDMI|snd[_-]|sound|hda.codec|hda.intel"
Feb 11 21:46:10 bettina-A8S-PRO kernel: ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
Feb 11 21:46:10 bettina-A8S-PRO kernel: pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Feb 11 21:46:10 bettina-A8S-PRO kernel: PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Feb 11 21:46:10 bettina-A8S-PRO kernel: software IO TLB: mapped [mem 0x000000006c3fd000-0x00000000703fd000] (64MB)
Feb 11 21:46:10 bettina-A8S-PRO kernel: integrity: Loaded X.509 cert 'Microsoft Corporation UEFI CA 2011: 13adbf4309bd82709c8cd54f316ed522988a1bd4'
Feb 11 21:46:10 bettina-A8S-PRO kernel: integrity: Loaded X.509 cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53'
Feb 11 21:46:10 bettina-A8S-PRO kernel: usb 1-2: Product: Microsoft® Nano Transceiver v2.0
Feb 11 21:46:10 bettina-A8S-PRO kernel: usb 1-2: Manufacturer: Microsoft
Feb 11 21:46:10 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.0/0003:045E:0745.0002/input/input5
Feb 11 21:46:10 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input0
Feb 11 21:46:10 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Mouse as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.1/0003:045E:0745.0003/input/input6
Feb 11 21:46:10 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.1/0003:045E:0745.0003/input/input7
Feb 11 21:46:10 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input1
Feb 11 21:46:10 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.2/0003:045E:0745.0004/input/input8
Feb 11 21:46:10 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 System Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.2/0003:045E:0745.0004/input/input10
Feb 11 21:46:10 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input2
Feb 11 21:46:10 bettina-A8S-PRO kernel: snd_hda_intel 0000:00:0e.0: dmic_detect option is deprecated, pass snd-intel-dspcfg.dsp_driver=1 option instead
Feb 11 21:46:10 bettina-A8S-PRO kernel: snd_hda_intel 0000:00:0e.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Feb 11 21:46:11 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: autoconfig for Generic: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
Feb 11 21:46:11 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Feb 11 21:46:11 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
Feb 11 21:46:11 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2:    mono: mono_out=0x0
Feb 11 21:46:11 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2:    dig-out=0x3/0x0
Feb 11 21:46:11 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2:    inputs:
Feb 11 21:46:11 bettina-A8S-PRO kernel: input: HDA Intel PCH HDMI as /devices/pci0000:00/0000:00:0e.0/sound/card0/input17
Feb 11 21:46:14 bettina-A8S-PRO kernel: snd_hda_intel 0000:00:0e.0: azx_get_response timeout, switching to polling mode: last cmd=0x20270503
Feb 11 21:46:15 bettina-A8S-PRO kernel: snd_hda_intel 0000:00:0e.0: No response from codec, disabling MSI: last cmd=0x20270503
Feb 11 21:46:16 bettina-A8S-PRO kernel: snd_hda_intel 0000:00:0e.0: azx_get_response timeout, switching to single_cmd mode: last cmd=0x20270503
Feb 11 21:46:17 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 21:46:17 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 21:46:39 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 21:46:39 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 21:48:39 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 21:48:39 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 22:06:53 bettina-A8S-PRO kernel: usb 1-2: Product: Microsoft® Nano Transceiver v2.0
Feb 11 22:06:53 bettina-A8S-PRO kernel: usb 1-2: Manufacturer: Microsoft
Feb 11 22:06:53 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.0/0003:045E:0745.0005/input/input18
Feb 11 22:06:53 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0005: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input0
Feb 11 22:06:53 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Mouse as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.1/0003:045E:0745.0006/input/input19
Feb 11 22:06:53 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.1/0003:045E:0745.0006/input/input20
Feb 11 22:06:53 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0006: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input1
Feb 11 22:06:53 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.2/0003:045E:0745.0007/input/input21
Feb 11 22:06:53 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 System Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.2/0003:045E:0745.0007/input/input23
Feb 11 22:06:53 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0007: input,hiddev0,hidraw3: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input2
Feb 11 22:07:04 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 22:07:04 bettina-A8S-PRO kernel: snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Feb 11 22:27:28 bettina-A8S-PRO kernel: usb 1-2: Product: Microsoft® Nano Transceiver v2.0
Feb 11 22:27:28 bettina-A8S-PRO kernel: usb 1-2: Manufacturer: Microsoft
Feb 11 22:27:28 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.0/0003:045E:0745.0008/input/input24
Feb 11 22:27:28 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0008: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input0
Feb 11 22:27:28 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Mouse as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.1/0003:045E:0745.0009/input/input25
Feb 11 22:27:28 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.1/0003:045E:0745.0009/input/input26
Feb 11 22:27:28 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.0009: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input1
Feb 11 22:27:28 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.2/0003:045E:0745.000A/input/input27
Feb 11 22:27:28 bettina-A8S-PRO kernel: input: Microsoft Microsoft® Nano Transceiver v2.0 System Control as /devices/pci0000:00/0000:00:15.0/usb1/1-2/1-2:1.2/0003:045E:0745.000A/input/input29
Feb 11 22:27:28 bettina-A8S-PRO kernel: hid-generic 0003:045E:0745.000A: input,hiddev0,hidraw3: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:15.0-2/input2
```

---

### Post by #&amp;thj^% on 2022-02-11
Thanks!
Wondering if you have a "Mute" hot-key as well.
It's vital that you upgrade Bios and Firmware. Boy this baby was truly written for Windows.
**Check that 'Secure Boot' and 'Fast Start' is disabled while your in there. Those settings will interfere with Linux if not changed.
Let me know when that's done. Thanks

---

### Post by #&amp;thj^% on 2022-02-12
I have not heard back from you.
A developer I know, not for any Debian OS's suggested adding this to "/etc/modprobe.d/alsa-base.conf"

```
sudo nano /etc/modprobe.d/alsa-base.conf 
```
And Add:
```
options snd-intel-dspcfg dsp_driver=1
```
If this is unsuccessful, Try a live installer version for 21.10 and while in the live session will your sound now work?

---

### Post by witherspoon2 on 2022-02-25
Ok, back on the topic. 
There is a mute-button on the keyboard but it works as expected. Pressing it puts the sound on mute or unmute.

Unfortunately I could not do the bios-update. The BIOS-menu does not offer an "update"-option. The Kuu-support-page for A8 brings me to a google-drive-folder with many files and folders and no explanation how to proceed. 

However  'Secure Boot' was and 'Fast Start' is now disabled.

Regarding firmware I did this:
```
fwupdmgr get-devices
A8S PRO
&#9474;
&#9500;&#9472;KUU-256GB:
&#9474;     Device ID:          c46944fe84f2b057692258cc87a812cc86364881
&#9474;     Summary:            ATA Drive
&#9474;     Current version:    T0910A0
&#9474;     Update Error:       No vendor ID set
&#9474;     GUIDs:              9395f5d3-e28f-5652-918a-706c8a1f8702
&#9474;                         ca24458b-4019-557b-a7a2-4ef6b0bb8058
&#9474;                         4cf0dd5d-f8e3-5613-ac1c-220fa04366a8
&#9474;     Device Flags:       &#8226; Internal device
&#9474;                         &#8226; System requires external power source
&#9474;                         &#8226; Needs a reboot after installation
&#9474;                         &#8226; Device is usable for the duration of the update
&#9474;   
&#9492;&#9472;System Firmware:
  &#9474;   Device ID:          15de43437c0f488c7ce84feace3720b6c9fac2a8
  &#9474;   Current version:    5
  &#9474;   Minimum Version:    5
  &#9474;   Vendor:             SHENZHEN YOUDISI E-COMMERCE CO. LTD (DMI:American Megatrends Inc.)
  &#9474;   GUIDs:              61fa5e0c-2119-40ae-a4e2-7672f3e60800
  &#9474;                       230c8b18-8d9b-53ec-838b-6cfc0383493a
  &#9474;                       a763a42e-eff1-5ce6-8576-5348f8b59b60
  &#9474;   Device Flags:       &#8226; Internal device
  &#9474;                       &#8226; Updatable
  &#9474;                       &#8226; System requires external power source
  &#9474;                       &#8226; Needs a reboot after installation
  &#9474;                       &#8226; Cryptographic hash verification is available
  &#9474;                       &#8226; Device is usable for the duration of the update
  &#9474; 
  &#9492;&#9472;UEFI dbx:
        Device ID:        362301da643102b9f38477387e2193e57abaa590
        Summary:          UEFI Revocation Database
        Current version:  83
        Minimum Version:  83
        Vendor:           UEFI:Linux Foundation
        Install Duration: 1 second
        GUIDs:            c6682ade-b5ec-57c4-b687-676351208742
                          f8ba2887-9411-5c36-9cee-88995bb39731
        Device Flags:     &#8226; Internal device
                          &#8226; Updatable
                          &#8226; Needs a reboot after installation
      
bettina@bettina-A8S-PRO:~$ fwupdmgr refresh
Updating lvfs
Downloading&#8230;             [***************************************]
Downloading&#8230;             [*                                      ] Less than oneDownloading&#8230;             [*                                      ] Less than oneDownloading&#8230;             [***************************************]
Successfully downloaded new metadata: 0 local devices supported
bettina@bettina-A8S-PRO:~$ fwupdmgr get-updates 
Devices with no available firmware updates: 
 &#8226; System Firmware
 &#8226; UEFI dbx
No updatable devices
bettina@bettina-A8S-PRO:~$ fwupdmgr update
Devices with no available firmware updates: 
 &#8226; System Firmware
 &#8226; UEFI dbx
No updatable devices
```

Adding this line does not change the situation, however deleting the already performed changes brought back the "Dummy-Output": 
```
options snd-intel-dspcfg dsp_driver=1
```

Started the OS from a live-ubuntu-USB but it only has "Dummy-Output".

---

### Post by badsha901 on 2022-04-05
Hello,

I have been facing exactly the same problem.
Please help me out.

---

### Post by #&amp;thj^% on 2022-04-06
Took me some time, but now a new test to try:
```
sudo nano  admin:///etc/pulse/default.pa
```
when it opens check for something like:
```
### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
```
change to this:(you will have your backup here when you paste that return here)
```
### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
load-module module-alsa-sink
load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
```
you'll notice the first two lines are now commented out.
Save and reboot.
**@badsha901 please open a new thread for your problem**, even if you think it's same as the OP's. Thanks

---

