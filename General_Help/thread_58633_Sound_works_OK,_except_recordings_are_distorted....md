---
title: "Sound works OK, except recordings are distorted..."
date: 2005-08-20
forum: General Help
---

### Post by mrowth on 2005-08-20
Kubuntu 5.04 Hoary Hedgehog i386, KDE 3.4.2, Motherboard: Asus A8V Deluxe, on-board VIA 2837 sound.

On the whole, sound seems to be working fine. Can have several applications play sound simultaneously, no problem.

Except that sound I *record* with Audacity or KWave is of unusably low quality - kind of hissy and tinny, distorted. (Same problem on SuSE 9.3, no problems on XP.)

Doesn't matter which sound device I'm recording from (KWave: /dev/dsp, /dev/audio, /dev/adsp; Audacity: there's only /dev/dsp). It also doesn't seem to matter which output device is used by the applications that I want to record the output of. The KDE Control Center (Sound & Multimedia: Sound System) has these to offer: Autodetect, OSS, ALSA, No I/O, ESD, Network Audio System, Threaded Open Sound System. That, too, doesn't seem to matter, except with regard to KDE system notification sounds. Or something. 

I read [http://audacityteam.org/wiki/index.pl?LinuxIssues](http://audacityteam.org/wiki/index.pl?LinuxIssues), installed assorted wxGTK packages, and compiled the latest stable release of Audactiy, configure'ing it "--with-portaudio=v19 --without-portmixer" as recommended. To my surprise, it actually compiled.

Now the preferences offer "OSS: /dev/dsp", "ALSA: VIA 8237" and "ALSA: Brooktree Bt878" as sound devices. "ALSA: VIA 8237" results in "Error while opening sound device. Please check the inpt device settings and the project sample rate." "OSS: /dev/dsp" works for both recording and playback, but recordings sound just as awful as before. 

Also, the waveform display is some two hundred pixels out of sync with the cursor, and there's no MP3 or Ogg support and no input selector on the toolbar (you know, the "Vol, Line in, Mic..." drop-down list). 

So I "make uninstall"ed it and reinstalled the Audacity 1.2.3-1 package via Synaptic.

I have no idea what ESD or Arts or ALSA or OSS or JACK or gstreamer or LADSPA (...) really are or do or which parts of which of them I need or in what way the relate to anything in /dev or, well, you get the idea: I'm barely above the level of "my sound thingie doesn't work" and pretty much nothing I found that seems to relate to my problem was written with that in mind. 

This may give you some hints:

KInfoCenter:
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux ... 2.6.10-5-386 #1 Thu Aug 18 22:23:56 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
VIA 8247 with ALC850 at 0xe800, irq 22
Brooktree Bt878 at 0xdff00000, irq 19

Audio devices:
0: VIA 2837 (DUPLEX)
1: Bt87x Digital

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC850 rev 0
1: Bt87x

```

"ALSA *emulation*"?  ](*,)  :-?  :confused: (etc.)

lsmod|grep snd:
```
snd_via82xx            25248  3
snd_ac97_codec         64608  1 snd_via82xx
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd_bt87x              12612  1
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  5 snd_via82xx,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  17 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_via82xx,snd_bt87x,snd_pcm

```

**Edit 1**

I've tried krecord, but recordings don't sound any better. And although Audacity exhibited the same symptoms there, Krecord worked fine back on SuSE. That's why I've not posted this as a hardware problem. 

I've tried Ardour, but it wants JACK.

I've tried JACK, but it says
"loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa"
I have no idea which application is using that or what the hell hw:0 is. The VIA 2837 maybe. Or 8247. Or 8237. Does that mean I mustn't use any other sound-using applications? Or start the jack daemon before any of them? RTFM, I know, I know. But there're way too many of these little things that don't really work and I never know what exactly's going wrong or which FM to R. 

I've tried Rosegarden, but it says 
"The Rosegarden sequencer could not be started, so sound and recording will be unavailable for this session.
For assistance with correct audio and MIDI configuration, go to http://rosegardenmusic.com."
Which I'm sure has nothing to do with anything anyway. After that, it crashes.

**Edit 2**

I've now installed whatever driver is in "realtek-linux-audiopack-3.3-2.tar.bz2", containing ALSA 1.0.9. Ran alsa-conf, soundcard was detected, everything went smoothly, but nothing's changed. Playing sound works like a charm, recording is staticy. (By "recording" I mean capturing the audio output.)

...

If anybody can help me pick a "real" soundcard... a cheap one... which is confirmed to actually work... please do so. I've got a stack of Soundblasters but it turned out they're all ISA cards.

Out of ideas again.

---

### Post by mrowth on 2005-08-21
This is the only time I'm going to bump this up, so please bear with me. Does anybody have *any* suggestions as to the nature of the problem?

I've tried krecord, but recordings don't sound any better.

I've tried Ardour, but it wants JACK.

I've tried JACK, but it says
"loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa"
I have no idea which application is using that or what the hell hw:0 is. The VIA 2837 maybe. Or 8247. Or 8237. Does that mean I mustn't use any other sound-using applications? Or start the jack daemon before any of them? RTFM, I know, I know. But there're way too many of these little things that don't really work and I never know what exactly's going wrong or which FM to R. 

I've tried Rosegarden, but it says 
"The Rosegarden sequencer could not be started, so sound and recording will be unavailable for this session.
For assistance with correct audio and MIDI configuration, go to http://rosegardenmusic.com."
Which I'm sure has nothing to do with anything anyway. After that, it crashes.


**Edit:** 

I've now installed whatever driver is in "realtek-linux-audiopack-3.3-2.tar.bz2", containing ALSA 1.0.9. Ran alsa-conf, soundcard was detected, everything went smoothly, but nothing's changed. Playing sound works like a charm, recording is staticy. (By "recording" I mean capturing the audio output.)

And although Audacity exhibited the same symptoms there, Krecord worked fine back on SuSE. That's why I've not posted this as a hardware problem. 

But if anybody can help me pick a "real" soundcard... a cheap one... which is confirmed to actually work... please do so. I've got a stack of Soundblasters but it turned out they're all ISA cards.

---

