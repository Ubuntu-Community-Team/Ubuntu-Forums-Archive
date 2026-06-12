---
title: "Suddenly my audio output is broke"
date: 2012-12-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-12-13
Playing error : GStreamer encountered a general stream error. at /usr/bin/../share/gmusicbrowser/gmusicbrowser_gstreamer-0.10.pm line 135.

```
~$ aplay .thunderbird/gotmail00.wav 
Playing WAVE '.thunderbird/gotmail00.wav' : Unsigned 8 bit, Rate 11000 Hz, Mono
ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: No such entity

aplay: set_params:1145: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  U8
SUBFORMAT:  STD
SAMPLE_BITS: 8
FRAME_BITS: 8
CHANNELS: 1
RATE: 11000
PERIOD_TIME: 125000
PERIOD_SIZE: 1375
PERIOD_BYTES: 1375
PERIODS: 4
BUFFER_TIME: 500000
BUFFER_SIZE: 5500
BUFFER_BYTES: 5500
TICK_TIME: [0 0]
```
edit:
some how i got it working, no idea why, just keep retrying the same fix tricks i had been trying (like deleting the .pulse cookie ant stuff)

---

