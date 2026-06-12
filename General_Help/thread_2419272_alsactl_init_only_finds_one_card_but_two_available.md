---
title: "alsactl init only finds one card but two available - sound wrong"
date: 2019-05-19
forum: General Help
---

### Post by thomas109 on 2019-05-19
Hi

I am having 2 soundcards:

```
sudo alsactl initFound hardware: "HDA-Intel" "Realtek ALC887-VD" "HDA:10ec0887,10438445,00100302" "0x1043" "0x8445"
Hardware is initialized using a generic method
```

but 2 cards are available:

```
 cat /proc/asound/cards >

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe300000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 19
```


when I try speaker-test with 

```
speaker-test -d hdmi:CARD=NVidia,DEV=1 -c 6 -t wav


```

```
speaker-test 1.1.3

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
Plug PCM: Route conversion PCM (sformat=S32_LE)
  Transformation table:
    0 <- 0
    1 <- 1
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 6
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  tstamp_type  : MONOTONIC
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Soft volume PCM
Control: PCM Playback Volume
min_dB: -51
max_dB: 0
resolution: 256
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  tstamp_type  : MONOTONIC
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  tstamp_type  : MONOTONIC
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 8192
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Hardware PCM card 0 'HD-Audio Generic' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : ENABLE
  tstamp_type  : MONOTONIC
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 4611686018427387904
  silence_threshold: 0
  silence_size : 4611686018427387904
  boundary     : 4611686018427387904
  appl_ptr     : 0
  hw_ptr       : 0
 0 - Front Left
 1 - Front Right
 2 - Unused



```


so I do not get sound to other than front channels.

Strangewise asound.conf is empty

no .asoundrec  defined.

anyone maybe has a hint why.

- there is a slave device used?
- where does the transformation table come from ?
- etc

Alsamixer is showing both devices
I selected Nvidia and died 
```
sudo alsactl store
```
but still speaker test uses the built in Card...


I also did a complete refresh of alsa by install kernal newly.


```

aplay -L 
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=Generic
    HD-Audio Generic, ALC887-VD Analog
    Default Audio Device
sysdefault:CARD=Generic
    HD-Audio Generic, ALC887-VD Analog
    Default Audio Device
front:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Front speakers
surround21:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Direct sample mixing device
dmix:CARD=Generic,DEV=1
    HD-Audio Generic, ALC887-VD Digital
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=1
    HD-Audio Generic, ALC887-VD Digital
    Direct sample snooping device
hw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=1
    HD-Audio Generic, ALC887-VD Digital
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC887-VD Analog
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=1
    HD-Audio Generic, ALC887-VD Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
```


Thanks t

---

### Post by thomas109 on 2019-05-19
Strangewise alsa wants to open a slave device, which I did not define? 
at least not as fas as I know of.....

appended:

```

speaker-test -c 6 -t wav -d hw:CARD=NVidia,DEV=3


speaker-test 1.1.3


Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory

:~$ speaker-test -c 6 -t wav -d hw:CARD=NVidia,DEV=7


speaker-test 1.1.3


Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory



```


asund.conf is very simple:
```

defaults.pcm.card 1
defaults.ctl.card 1


 

```

updated to:

```
pcm.snd_card {
    type hw
    card 1
    device 7
}


ctl.snd_card {
    type hw
    card 1
    device 7
}


pcm.!default {
    type plug
    slave.pcm "snd_card"
}
```

give sound with vlc 

but speakter-test will not send sound to other than center...

Thanks

---

