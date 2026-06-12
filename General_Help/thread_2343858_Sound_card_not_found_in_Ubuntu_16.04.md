---
title: "Sound card not found in Ubuntu 16.04"
date: 2016-11-19
forum: General Help
---

### Post by chocalopix on 2016-11-19
Hello everyone, 
I have the Acer Aspire E5-575G  where no sound card is found with ```
aplay -l 
``` .I have also added myself in audio group and reinstalled modules with 
  ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2 

```  The problem though seems to be deeper. From that moment I upgraded kernel from ***4.4*** to ***4.8*** without any result.

  From ```
lspci | grep "Audio" I get 
```

  ```
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)

```  and this is my ```
/sbin/lsmod | grep snd output
```

  ```
snd_seq_dummy          16384  2
snd_soc_skl            65536  0
snd_soc_skl_ipc        40960  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        28672  1 snd_soc_skl_ipc
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
snd_soc_core          233472  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          36864  0
snd_hda_codec         135168  1 snd_hda_intel
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  9 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    86016  12 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_seq_device,snd_soc_core,snd_pcm
soundcore              16384  1 snd

```  My knowledge in Linux is relatively small and I do not know what to  do next. There is no difference with the live CD. Thanks for any input.

---

