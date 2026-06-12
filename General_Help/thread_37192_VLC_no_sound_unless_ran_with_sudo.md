---
title: "VLC no sound unless ran with sudo"
date: 2005-05-26
forum: General Help
---

### Post by logan2004 on 2005-05-26
```
joe@whs-0994:~$ vlc systm--0001--warspyingbox--large.xvid.avi
VLC media player 0.8.1 Janus
[00000272] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:32
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver returned error: Permission denied
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings

```

but it plays nice with sudo...

```

joe@whs-0994:~$ sudo vlc systm--0001--warspyingbox--large.xvid.avi
VLC media player 0.8.1 Janus
[00000272] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:32

```

any ideas???

---

### Post by bored2k on 2005-05-26
[QUOTE=logan2004]```
joe@whs-0994:~$ vlc systm--0001--warspyingbox--large.xvid.avi
VLC media player 0.8.1 Janus
[00000272] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:32
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver returned error: Permission denied
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings

```

but it plays nice with sudo...

```

joe@whs-0994:~$ sudo vlc systm--0001--warspyingbox--large.xvid.avi
VLC media player 0.8.1 Janus
[00000272] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:32

```

any ideas???[/QUOTE]
 Are you using alsa or esd ? try installing vlc-esd vlc-alsa and configuring it in vlc's preferences.

---

