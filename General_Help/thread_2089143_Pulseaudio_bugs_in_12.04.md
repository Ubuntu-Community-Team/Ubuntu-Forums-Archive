---
title: "Pulseaudio bugs in 12.04"
date: 2012-11-28
forum: General Help
---

### Post by ImTheBatman on 2012-11-28
Hi, I am using ubuntu 12.04.1 and I am experiencing a problem with pulseaudio. When playing music, video games or anything else that uses sound, every once in a few minutes the sound gets chunked for less than a second. I tried changing some bitrate configurations in pulseaudio's conf file, and that caused the chunking to be replaced with a buzzing sound at that moment.

Pulseaudio logs clearly show an error with 'snd_hda_intel':
```
( 349.592|  58.650) E: [alsa-sink] alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 58256 bytes (330 ms).
( 349.592|  58.650) E: [alsa-sink] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: snd_pcm_dump():
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: Soft volume PCM
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: Control: PCM Playback Volume
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: min_dB: -51
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: max_dB: 0
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: resolution: 256
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: Its setup is:
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   stream       : PLAYBACK
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   access       : MMAP_INTERLEAVED
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   format       : S16_LE
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   subformat    : STD
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   channels     : 2
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   rate         : 44100
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   exact rate   : 44100 (44100/1)
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   msbits       : 16
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   buffer_size  : 352
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_size  : 44
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_time  : 997
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   tstamp_mode  : ENABLE
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_step  : 1
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   avail_min    : 44
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_event : 1
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   start_threshold  : -1
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   stop_threshold   : 1476395008
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   silence_threshold: 0
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   silence_size : 0
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   boundary     : 1476395008
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
( 349.592|   0.000) E: [alsa-sink] alsa-util.c: Its setup is:
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   stream       : PLAYBACK
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   access       : MMAP_INTERLEAVED
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   format       : S16_LE
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   subformat    : STD
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   channels     : 2
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   rate         : 44100
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   exact rate   : 44100 (44100/1)
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   msbits       : 16
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   buffer_size  : 352
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_size  : 44
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_time  : 997
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   tstamp_mode  : ENABLE
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_step  : 1
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   avail_min    : 44
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   period_event : 1
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   start_threshold  : -1
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   stop_threshold   : 1476395008
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   silence_threshold: 0
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   silence_size : 0
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   boundary     : 1476395008
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   appl_ptr     : 13925121
( 349.592|   0.000) E: [alsa-sink] alsa-util.c:   hw_ptr       : 13939333
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -42908 bytes (-243 ms).
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: snd_pcm_dump():
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: Soft volume PCM
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: Control: PCM Playback Volume
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: min_dB: -51
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: max_dB: 0
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: resolution: 256
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: Its setup is:
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   stream       : PLAYBACK
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   access       : MMAP_INTERLEAVED
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   format       : S16_LE
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   subformat    : STD
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   channels     : 2
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   rate         : 44100
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   exact rate   : 44100 (44100/1)
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   msbits       : 16
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   buffer_size  : 352
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_size  : 44
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_time  : 997
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   tstamp_mode  : ENABLE
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_step  : 1
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   avail_min    : 44
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_event : 1
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   start_threshold  : -1
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   stop_threshold   : 1476395008
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   silence_threshold: 0
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   silence_size : 0
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   boundary     : 1476395008
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
( 349.593|   0.000) E: [alsa-sink] alsa-util.c: Its setup is:
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   stream       : PLAYBACK
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   access       : MMAP_INTERLEAVED
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   format       : S16_LE
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   subformat    : STD
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   channels     : 2
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   rate         : 44100
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   exact rate   : 44100 (44100/1)
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   msbits       : 16
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   buffer_size  : 352
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_size  : 44
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_time  : 997
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   tstamp_mode  : ENABLE
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_step  : 1
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   avail_min    : 44
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   period_event : 1
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   start_threshold  : -1
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   stop_threshold   : 1476395008
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   silence_threshold: 0
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   silence_size : 0
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   boundary     : 1476395008
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   appl_ptr     : 13928641
( 349.593|   0.000) E: [alsa-sink] alsa-util.c:   hw_ptr       : 13939376
( 349.594|   0.001) I: [alsa-sink] alsa-sink.c: Underrun!
```But I don't know how to fix it. Any help?

---

### Post by ImTheBatman on 2012-11-28
help anybody?

---

### Post by ImTheBatman on 2012-11-28
If I disable pulseaudio (via autospawn = no in client.conf) and use ALSA instead, it seems to work fine. So this is a pulseaudio specific problem.

---

