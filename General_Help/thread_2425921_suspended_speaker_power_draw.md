---
title: "suspended speaker power draw"
date: 2019-09-02
forum: General Help
---

### Post by n2eee on 2019-09-02
Good morning/afternoon/night,

I recently purchased an Acer Travelmate P6 (TMP614-51-50FJ) and decided to try xubuntu (19.04) out for the first time. After using it for a few days, I noticed that when the laptop was suspended, the current consumption was pretty significant, about 6% of the battery per hour. This also happens when the laptop is on. After some analysis with a thermal camera, it looked to be the speakers. When connected to an oscilloscope, there seems to be a 1.25 MHz 13 Vpeak square wave on either one or both of the speakers. When launching windows, this problem does not happen. This issue causes a 2-4 watt power draw from the speakers alone, and a change of 30 f (17 c) from ambient, shortening the battery life significantly, and possibly damaging the speakers.

I am absolutely clueless on how to start looking into this. Any information or even a direction to start in would be greatly appreciated.

Thank you
-N2EEE

---

### Post by n2eee on 2019-09-02
After some investigation, it appears to be an issue with suspending the speakers. After 6 seconds of not playing sound, the issue begins. 
Executing this appears to fix it temporarily.
```
echo "on" > /sys/bus/hdaudio/drivers/snd_hda_codec_realtek/hdaudioC0D0/power/control
``` 
Now the issue is there's a very audible 17 KHz wine, and it does not work during sleep.
some system info:
```
matt@matt-Linux:~$ lspci | grep udio
00:1f.3 Multimedia audio controller: Intel Corporation Device 9dc8 (rev 30)
```
```
matt@matt-Linux:~$ grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC295
/proc/asound/card0/codec#2:Codec: Intel Kabylake HDMI

```
```

matt@matt-Linux:~$  inxi -A
Audio:     Device-1: Intel driver: snd_hda_intel
           Sound Server: ALSA v: k5.0.0-27-generic 

```
```
matt@matt-Linux:~$  lsmod | grep snd
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_soc_skl           106496  0
snd_soc_hdac_hda       24576  1 snd_soc_skl
snd_hda_ext_core       28672  2 snd_soc_hdac_hda,snd_soc_skl
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_soc_sst_ipc        20480  1 snd_soc_skl_ipc
snd_soc_sst_dsp        36864  1 snd_soc_skl_ipc
snd_soc_acpi_intel_match    28672  1 snd_soc_skl
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_soc_skl
snd_soc_core          233472  2 snd_soc_hdac_hda,snd_soc_skl
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          40960  3
snd_hda_codec         131072  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
snd_hda_core           86016  8 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_hdac_hda,snd_soc_skl
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd



```

---

