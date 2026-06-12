---
title: "I broke my audio drivers..."
date: 2015-12-08
forum: General Help
---

### Post by tsault on 2015-12-08
So I hooked up my old 5.1 logitech speakers and wanted a more fully featured audio mixer as they were going crazy with the bass, tried installing alsa drivers etc. and I've either missed a step, not noticed an error or have some compatibility problem. Usually I manage to figure out what library I'm missing with a quick google but not getting anywhere today so any advice would be much appreciated.

Before messing with stuff pulse audio controller worked fine and both the onboard and gpu audio cards were showing up in system settings>sound, now I just get Dummy Output which obviously doesn't work. Also, I can't open alsamixer or the other alsa utilities through terminal, it returns this error:
alsamixer
alsamixer: /usr/lib/x86_64-linux-gnu/libasound.so.2: version `ALSA_1.0.10' not found (required by alsamixer)
similar error with different versions for amixer, aplay etc.

Alsainfo [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) returns this
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Wed Dec  9 02:54:59 UTC 2015




!!Linux Distribution
!!------------------


Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:      System manufacturer
Product Name:      P5Q
Product Version:   System Version
Firmware Version:  1104   




!!Kernel Information
!!------------------


Kernel release:    3.13.0-71-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     
Library version:    1.1.0
Utilities version:  




!!Loaded ALSA modules
!!-------------------






!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------






!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Barts HDMI Audio [Radeon HD 6800 Series]




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1b.0 0403: 8086:3a3e
    Subsystem: 1043:82fe
--
01:00.1 0403: 1002:aa88
    Subsystem: 1787:aa88




!!Modprobe options (Sound related)
!!--------------------------------


snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------




!!ALSA Device nodes
!!-----------------


crw-rw---- 1 root audio 116, 1 Dec  9 13:10 /dev/snd/seq




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: /usr/lib/x86_64-linux-gnu/libasound.so.2: version `ALSA_1.0.14' not found (required by aplay)


ARECORD


arecord: /usr/lib/x86_64-linux-gnu/libasound.so.2: version `ALSA_1.0.14' not found (required by arecord)


!!Amixer output
!!-------------




!!Alsactl output
!!--------------


--startcollapse--
--endcollapse--




!!All Loaded Modules
!!------------------


Module
nls_utf8
isofs
cuse
bnep
rfcomm
bluetooth
joydev
kvm_intel
kvm
serio_raw
lpc_ich
fglrx
asus_atk0110
mac_hid
amd_iommu_v2
shpchp
parport_pc
ppdev
hwmon_vid
coretemp
lp
parport
hid_generic
usbhid
hid
floppy
psmouse
pata_marvell
firewire_ohci
ahci
libahci
firewire_core
pata_acpi
crc_itu_t
atl1e




!!ALSA/HDA dmesg
!!--------------



```

Any hints on what I may have missed or other diagnostics to run? Although I'm not computer illiterate I'm not exactly fluent in Ubuntu either so I'll probably need verbose instructions for stuff beyond bash commands.

---

