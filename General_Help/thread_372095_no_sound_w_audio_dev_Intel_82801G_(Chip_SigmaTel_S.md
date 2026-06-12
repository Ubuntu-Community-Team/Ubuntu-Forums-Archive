---
title: "no sound w/ audio dev Intel 82801G (Chip: SigmaTel STAC9274D)"
date: 2007-02-27
forum: General Help
---

### Post by inCursorated on 2007-02-27
Hello. I recently purchased a new Intel D975XBX2 motherboard. Everything is working great (including Beryl and WoW) *except* the audio - i have yet to hear a peep out of my speakers. I found [this page]("https://help.ubuntu.com/community/HdaIntelSoundHowto") which really hasn't helped... i've tried various options to /etc/modprobe.d/alsa-base with no change. this is the only error i've come across:

```
zeus@mt-olympus:~$ speaker-test

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
```

i tried to install the latest alsa driver and got this:
```
root@mt-olympus:/usr/src/alsa/alsa-driver-1.0.14rc2# dpkg -i alsa-driver_1.0.14rc2-1_i386.deb
(Reading database ... 139829 files and directories currently installed.)
Unpacking alsa-driver (from alsa-driver_1.0.14rc2-1_i386.deb) ...
dpkg: error processing alsa-driver_1.0.14rc2-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.17-11-generic/modules.alias', which is also in package linux-image-2.6.17-11-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 alsa-driver_1.0.14rc2-1_i386.deb
root@mt-olympus:/usr/src/alsa/alsa-driver-1.0.14rc2#
```

following is some more info i've gathered... can anyone help?

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Chip: SigmaTel STAC9274D  


00:1b.0 0403: 8086:27d8 (rev 01)
        Subsystem: 8086:0419
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at 92300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

zeus@mt-olympus:~$ lsmod | grep snd
snd_hda_intel          20116  3
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_pcm                84612  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    58372  15 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.11 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                                          &#9474;
&#9474; Chip: SigmaTel STAC9274D                                                                                                                 &#9474;
&#9474; View: [Playback] Capture  All                                                                                                            &#9474;
&#9474; Item: PCM    

zeus@mt-olympus:/dev$ ls -l sndstat
lrwxrwxrwx 1 root root 24 2007-02-26 00:24 sndstat -> /proc/asound/oss/sndstat
zeus@mt-olympus:/dev$ cat sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux mt-olympus 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0x92300000 irq 58

Audio devices:
0: STAC92xx Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: SigmaTel STAC9274D

zeus@mt-olympus:~$ asoundconf list
Names of available sound cards:
Intel

zeus@mt-olympus:/proc/asound$ cat versions
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
```

---

### Post by inCursorated on 2007-02-28
i ran asoundconf reset-default-card
followed by  asoundconf set-default-card Intel

now it looks like it's working but i still don't hear anything :( 

```

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
Time per period = 2.662804
 0 - Front Left
Time per period = 2.986647
 0 - Front Left
Time per period = 2.986660
 0 - Front Left

```

---

### Post by kuja on 2008-04-02
Works more or less in Hardy for me with an Intel DX38BT board, same audio chip. I can't get sound out of my rear speakers though no matter what I do.

---

### Post by kuja on 2008-04-02
Wait a minute ...... On a hunch I connected different speakers .... sound out of the rear speakers does work. Perhaps it's actually a speaker problem.

---

### Post by mrhealthpatriot on 2008-06-30
Try "solution G" at
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

