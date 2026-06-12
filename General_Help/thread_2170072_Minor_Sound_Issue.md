---
title: "Minor Sound Issue"
date: 2013-08-24
forum: General Help
---

### Post by swhit3 on 2013-08-24
Using 13.04 64-bit, (Linux kernel version 3.8.0-27-generic) on an Asus u56e laptop. My sound is having some issues. Whenever I adjust the volume higher/lower my speakers/headphones make a sort of crackling noise. It's not very noticeable when I'm playing music or watching a video, but when I adjust the volume with no sounds playing I can clearly hear a distinct crackle sound. It also appears to crackle randomly as well every couple of minutes, but I can only duplicate the issue when I raise or lower my volume.  


Here is the output from lspci -v | grep -A7 -i "audio"

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1bd3
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at dfc00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
```


And also the output from sudo aplay -l

    ```
**** List of PLAYBACK Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
      Subdevices: 0/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
```


Output results of sudo aplay -L

```
default
        Playback/recording through the PulseAudio sound server
    sysdefault:CARD=PCH
        HDA Intel PCH, ALC269VB Analog
        Default Audio Device
    front:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        Front speakers
    surround40:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        4.0 Surround output to Front and Rear speakers
    surround41:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        4.1 Surround output to Front, Rear and Subwoofer speakers
    surround50:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        5.0 Surround output to Front, Center and Rear speakers
    surround51:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        5.1 Surround output to Front, Center, Rear and Subwoofer speakers
    surround71:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
    hdmi:CARD=PCH,DEV=0
        HDA Intel PCH, HDMI 0
        HDMI Audio Output
    dmix:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        Direct sample mixing device
    dmix:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Direct sample mixing device
    dsnoop:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Direct sample snooping device
    hw:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Direct hardware device without any conversions
    plughw:CARD=PCH,DEV=0
        HDA Intel PCH, ALC269VB Analog
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Hardware device with all software conversions
``` 


Lastly, here is what my alsa-base.conf file looks like since I have tried editing it before, it's no longer default settings.

```
# autoloader aliasesinstall sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=basic
```

These outputs were posted to show the sound card in my laptop. 
I have tried some troubleshooting techniques here: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting) however they did not resolve the issue. 
Any help with this issue would be greatly appreciated. Thanks for any help in advance!

---

### Post by swhit3 on 2013-09-01
It's been a week now, still experiencing the same issue. Any thoughts or suggestions?
Hope everyone is enjoying their Labor Day weekend!

---

### Post by CatKiller on 2013-09-01
It's possible that it's a software issue I suppose, but have you tried switch cleaner?

---

