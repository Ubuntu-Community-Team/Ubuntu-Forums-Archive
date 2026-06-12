---
title: "Complex ALSA Audio issues"
date: 2013-02-04
forum: General Help
---

### Post by changlinn on 2013-02-04
Recently I ran a dist-upgrade on my media box recently and audio stopped working, came up with Null device on reboot. I used to use the onboard audio and VGA from the Nvidia card to TV, but during trying to fix this I have decided to move to the HDMI, but now neither works for audio. Interestingly when I first started this the output of /proc/asound/cards and aplay -l had my onboard intel but now it doesn't (see below). Basically I would like to get this back to some state of audio working, even if I have to go back to VGA and 3.5mm audio...
Interestingly aplay test.wav plays but no sound comes out, neither does it come out on mplayer test.mp4
I have the computer plugged in to a port on the tv that works for our digital video camera for audio so I doubt it is the TV, could be the cable which is why I am basically asking how to get it back to detecting the intel on board audio.

I am running the below
ASUS 512MB GT210 PCI-E VGA Card
Asus p6t motherboard
Core i7
Ubuntu 12.04

I tried this guide [here]("http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240") to no avail, I also may have used other forum posts that have caused this issue, I do actually remember putting in hw:0,3 somewhere but I can't recall where.

My user is a member of the audio group, but when I try and play audio now via aplay I get;

```
$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbafc000 irq 24

```

Outputs;
```
$lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
```


```
$ cat /etc/alsa/alsa-source.conf 
### ALSA source configuration file ###
# (This file is in GNU makefile format)

# List the card drivers to be built, separated by commas. For example,
# if you want to build the drivers for the Sound Blaster 16 and the
# Yamaha YMF cards then write:
#     ALSA_CARDS="sb16, ymfpci"
# The special name "all" results in all card drivers being built.
#
ifndef ALSA_CARDS
ALSA_CARDS="all"
endif

# List the card driver options, separated by commas, all on one line.
# The special name "all" results in all possible options being set.
#
# This is an advanced feature.  See ALSA's documentation for more info.
#
ifndef ALSA_CARD_OPTIONS
ALSA_CARD_OPTIONS=""
endif

# Set to "y" if you want to build the modules without ISA PnP support.
# Otherwise, set to "".
#
ifndef ALSA_NOPNP
ALSA_NOPNP=""
endif

# Set to "y" if you want to build the modules with debugging code.
# Otherwise, set to "".
#
ifndef ALSA_DEBUG
ALSA_DEBUG=""
endif
media@stu2:~$ cat /etc/modprobe.d/alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
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

options snd-hda-intel enable_msi=0 probe_mask=0xfff2

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

```
$ cat /etc/modprobe.d/sound.conf 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

```

```
$ dpkg -l |grep -i alsa
ii  aconnectgui                                    0.9.0rc2-1-9                                 graphical ALSA sequencer connection manager
ii  alsa-base                                      1.0.24+dfsg-0ubuntu2                         ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.24.1-0ubuntu1                            ALSA software loaders for specific hardware
ii  alsa-hda-dkms                                  0.201211291615~oneiric1                      HDA driver in DKMS format.
ii  alsa-oss                                       1.0.17-5                                     ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.24+dfsg-0ubuntu2                         ALSA driver sources
ii  alsa-tools                                     1.0.24.1-0ubuntu1                            Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                 1.0.24.1-0ubuntu1                            GUI based ALSA utilities for specific hardware
ii  alsa-utils                                     1.0.24.2-0ubuntu8.1                          Utilities for configuring and using ALSA
ii  bluez-alsa                                     4.96-0ubuntu4                                Bluetooth ALSA support
ii  gstreamer0.10-alsa                             0.10.35-1                                    GStreamer plugin for ALSA
rc  lib32asound2                                   1.0.24.1-0ubuntu10                           shared library for ALSA applications (32 bit)
ii  libasound2                                     1.0.24.1-0ubuntu10                           shared library for ALSA applications
ii  libasound2:i386                                1.0.24.1-0ubuntu10                           shared library for ALSA applications
ii  libasound2-dev                                 1.0.24.1-0ubuntu10                           shared library for ALSA applications -- development files
ii  libasound2-plugins                             1.0.24-0ubuntu6.1                            ALSA library additional plugins
ii  libasound2-plugins:i386                        1.0.24-0ubuntu6.1                            ALSA library additional plugins
ii  libsox-fmt-alsa                                14.3.2-1ubuntu1                              SoX alsa format I/O library
rc  linux-backports-modules-alsa-2.6.32-24-generic 2.6.32-24.17                                 Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  linux-sound-base                               1.0.24+dfsg-0ubuntu2                         base package for ALSA and OSS sound systems

```

---

### Post by Yellow Pasque on 2013-02-04
This line looks suspect (like it randomly got inserted in the middle of the alsa-base.conf file):
```
options snd-hda-intel enable_msi=0 probe_mask=0xfff2
```
I would try removing it and rebooting (or running sudo alsa force-reload). Then post alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> My user is a member of the audio group
That's not necessary and is a bad idea: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by changlinn on 2013-02-05
Can't believe I missed that, I made that change during my attempts to fix it. Thank you so much, first time HDMI audio has worked.

---

