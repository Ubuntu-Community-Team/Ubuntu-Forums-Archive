---
title: "sound help"
date: 2014-03-23
forum: General Help
---

### Post by skibum3027 on 2014-03-23
Right now I have no sound :( I'd like to get both the analog output and hdmi audio (integrated, not a video card) working.

So far, the most helpful forum post/wiki article I've found is [http://wiki.bodhilinux.com/doku.php?id=alsa_index](http://wiki.bodhilinux.com/doku.php?id=alsa_index)

My system is actually running Bodhi Linux, but as it's an Ubuntu derivative, so I'm hoping someone here can help.

some potentially relevant outputs:

```
####@####-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


####@####-PC:~$ lspci | grep Audio
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)



####@####-PC:~$ lsmod | grep snd
snd_hda_codec_realtek    79916  1
snd_hda_codec_hdmi     37434  1
snd_hda_intel          44339  5
snd_hda_codec         141716  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    69533  19 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm


####@####-PC:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Intel Haswell HDMI







```


Any chance someone can point me in the right direction please???

---

