---
title: "Help getting XonarDG Audio"
date: 2015-02-21
forum: General Help
---

### Post by jeff115 on 2015-02-21
Hi,

My speakers won't play from the back port of the Xonar DG in Ubuntu 14.10. Speakers play from motherboard out and headphones from the front panel. If it means anything, I tried on both Gnome desktop and KDE - no change. Please let me know what to try.

```

jeff@hyrule:~$ modprobe snd_oxygen
jeff@hyrule:~$ 

```

```

jeff@hyrule:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k3.16.0-30-generic.

```

```

jeff@hyrule:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfb620000 irq 62
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfb080000 irq 18
 2 [DG             ]: CMI8786 - Xonar DG
                      C-Media Oxygen HD Audio at 0xc000, irq 18

```              

```

jeff@hyrule:~$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0]   : control
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 2]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 1]   : control
  9: [ 1- 3]: digital audio playback
 10: [ 1- 7]: digital audio playback
 11: [ 1- 8]: digital audio playback
 12: [ 1- 9]: digital audio playback
 13: [ 1- 0]: hardware dependent
 14: [ 1- 1]: hardware dependent
 15: [ 1- 2]: hardware dependent
 16: [ 1- 3]: hardware dependent
 17: [ 2]   : control
 18: [ 2- 0]: digital audio playback
 19: [ 2- 0]: digital audio capture
 20: [ 2- 1]: digital audio playback
 21: [ 2- 1]: digital audio capture
 33:        : timer
 
```

```

jeff@hyrule:~$ cat /proc/asound/pcm
00-00: ALC892 Analog : ALC892 Analog : playback 1 : capture 1
00-01: ALC892 Digital : ALC892 Digital : playback 1
00-02: ALC892 Alt Analog : ALC892 Alt Analog : capture 1
01-03: HDMI 0 : HDMI 0 : playback 1
01-07: HDMI 0 : HDMI 0 : playback 1
01-08: HDMI 0 : HDMI 0 : playback 1
01-09: HDMI 0 : HDMI 0 : playback 1
02-00: Multichannel : Multichannel : playback 1 : capture 1
02-01: Digital : Digital : playback 1 : capture 1

```

```

jeff@hyrule:~$ cat /proc/asound/timers
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P1-3-0: PCM playback 1-3-0 : SLAVE
P1-7-0: PCM playback 1-7-0 : SLAVE
P1-8-0: PCM playback 1-8-0 : SLAVE
P1-9-0: PCM playback 1-9-0 : SLAVE
P2-0-0: PCM playback 2-0-0 : SLAVE
P2-0-1: PCM capture 2-0-1 : SLAVE
P2-1-0: PCM playback 2-1-0 : SLAVE
P2-1-1: PCM capture 2-1-1 : SLAVE

```

```

jeff@hyrule:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_oxygen
 
```
 
```

jeff@hyrule:~$ lsmod | grep snd
snd_hda_codec_hdmi     47547  4 
snd_oxygen             25211  3 
snd_oxygen_lib         41369  1 snd_oxygen
snd_mpu401_uart        14169  1 snd_oxygen_lib
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec_realtek    76887  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_realtek
snd_rawmidi            30876  2 snd_mpu401_uart,snd_seq_midi
snd_hda_intel          30420  5 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104102  6 snd_hda_codec_hdmi,snd_oxygen_lib,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29513  2 snd_pcm,snd_seq
snd                    87611  29 snd_oxygen,snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_oxygen_lib,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device
soundcore              15052  2 snd,snd_hda_codec

```

---

