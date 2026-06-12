---
title: "pulseaudio, recordmydesktop"
date: 2008-05-22
forum: General Help
---

### Post by Azzco on 2008-05-22
Hello, I've been messing around with recordmydesktop a bit the last few days now. Mostly compiz but now I want to record a game and I need to have sound working too. First I thought it'd be no problms just ticking for sound in gtk-recordmydesktop.

But I get a error, so I tried without the gui, ```
Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device
```This is really troublesome, so I tried with ```
padsp recordmydesktop -device /dev/dsp
```But that didn't help a bit.```
Buffer size adjusted to 4096 from 4096 frames.
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
Couldn't open PCM device /dev/dsp
Error while opening/configuring soundcard /dev/dsp
Try running with the --no-sound or specify a correct device.

```
Will I need to tell recordmydesktop that it should look for oss devices instead?

Also I know that my sound input is set up correctly as I can record sounds with audacity properly. (Using 'padsp audacity' of course.)

---

### Post by go_beep_yourself on 2009-08-19
[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

---

