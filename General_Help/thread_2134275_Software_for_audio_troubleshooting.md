---
title: "Software for audio troubleshooting"
date: 2013-04-10
forum: General Help
---

### Post by grey1beard on 2013-04-10
For some time I've been wanting and trying to set up my laptop, running 12.04LTS, to act as a sort of audio experimenters tool shop.
What I need is to be able to plug in hardware like mics, sound generators that I've built, musical instruments etc,  into the laptop, to observe waveforms in the audio range with a software scope, and thus be able to troubleshoot the input devices.
I installed xoscope, to make use of the onboard sound card [Intel 82801DB-ICH4] but have run into the problem** /dev/dsp not found**, and have not yet found any posting that explains how to get round this, though a lot of old threads mention this as a stumbling block.(Perhaps someone could enlighten me as to what 'dsp' is referring to ?)

If there is no solution to getting xoscope to run in 12.04, perhaps an alternative might be suggested. 
Being able to put a signal on the X and Y 'plates' (in order to generate lissajous figures) would be more useful than multiple channels - 2 would be enough !

Recording the signals would be the next desirable step, but as yet I see no need for anything more.
If I can get this far, I shall be more than pleased, but if more than one package is involved, then help in interconnecting them would almost certainly be needed !

John

---

### Post by tgalati4 on 2013-04-10
It's possible that xoscope was written using the OSS audio framework and that uses /dev/dsp as the sound device.  If you have OSS installed on your system then you should have a /dev/dsp.

```
dpkg -l |egrep "pulse|alsa|oss-"c
```

tgalati4@Mint14-Extensa ~ $ apt-cache search OSS audio
.
.
oss4-base - Open Sound System - base package
oss4-gtk - Open Sound System - simple GTK2-based mixer control

It's not installed in 12.10 by default:

tgalati4@Mint14-Extensa ~ $ apt-cache policy oss4-base
oss4-base:
  Installed: (none)
  Candidate: 4.2-build2005-2ubuntu1
  Version table:
     4.2-build2005-2ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

---

### Post by grey1beard on 2013-04-11
Thanks  tgalati4. Though not a Terminal whiz, I read your post as an instruction to find what I had re alsa, pulseaudio, and OSS, and got the following - 

> john@john-Satellite-A30:~$ dpkg -l |egrep "pulse|alsa|oss-"c
ii  alsa-base                              1.0.25+dfsg-0ubuntu1.1                  ALSA driver configuration files
ii  alsa-utils                             1.0.25-1ubuntu5                         Utilities for configuring and using ALSA
ii  alsaplayer-alsa                        0.99.80-5build1                         PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                      0.99.80-5build1                         PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                         0.99.80-5build1                         PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                             4.98-2ubuntu7                           Bluetooth ALSA support
ii  gstreamer0.10-alsa                     0.10.36-1ubuntu0.1                      GStreamer plugin for ALSA
ii  gstreamer0.10-pulseaudio               0.10.31-1ubuntu1.2                      GStreamer plugin for PulseAudio
ii  libcanberra-pulse                      0.28-3ubuntu3                           PulseAudio backend for libcanberra
ii  libpulse-mainloop-glib0                1:1.1-0ubuntu15.2                       PulseAudio client libraries (glib support)
ii  libpulse0                              1:1.1-0ubuntu15.2                       PulseAudio client libraries
ii  libpulsedsp                            1:1.1-0ubuntu15.2                       PulseAudio OSS pre-load library
ii  oss-compat                             1                                       Open Sound System (OSS) compatibility package
ii  pulseaudio                             1:1.1-0ubuntu15.2                       PulseAudio sound server
ii  pulseaudio-esound-compat               1:1.1-0ubuntu15.2                       PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth            1:1.1-0ubuntu15.2                       Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf                1:1.1-0ubuntu15.2                       GConf module for PulseAudio sound server
ii  pulseaudio-module-x11                  1:1.1-0ubuntu15.2                       X11 module for PulseAudio sound server
ii  pulseaudio-utils                       1:1.1-0ubuntu15.2                       Command line tools for the PulseAudio sound server
ii  vlc-plugin-pulse                       2.0.5-0ubuntu0.12.04.1                  PulseAudio plugin for VLC
john@john-Satellite-A30:~$ 


I used your *apt-cache search OSS audio* got the same back as you -
> .....
oss4-base - Open Sound System - base package
oss4-gtk - Open Sound System - simple GTK2-based mixer control


Likewise using *apt-cache policy oss4-base*, I got -

> oss4-base:
  Installed: (none)
  Candidate: 4.2-build2005-2ubuntu1
  Version table:
     4.2-build2005-2ubuntu1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

Is your advice that I should try installing OSS ? If so, do I need to remove any of the alsa or pulseaudio packages ?
Wondering that if this is so, it might upset any other installed software audio ?

Regards
John

---

### Post by kostkon on 2013-04-11
> **grey1beard said:**
> Wondering that if this is so, it might upset any other installed software audio ?
It will... maybe a lot.

I think it's not sensible to totally replace your audio stack for just one application.

Try running it with padsp, i.e.:
```
padsp xoscope
```
or whatever the executable is called.

---

### Post by grey1beard on 2013-04-11
Hi kostkon.
Good idea, and it worked. At least it didn't give me the /dev/dsp not found error !
All I have to do now is try and work out how to use it.
As I find nothing in the gui that bears much resemblance to hardware scopes that I am familiar with, that may take some doing.
At the moment I've just got a mic plugged in, checked my sound settings are set to mic, no mutes anywhere, but no trace.
So I'll have to play for a while.
Regards
John

---

### Post by gordintoronto on 2013-04-11
I installed Xoscope 2.0-3.1 using Synaptic. Software Center should be the same.

Can you record sound with Sound Recorder? When I ran it, I needed to jack up the input volume control, and then padsp xoscope produced nice oscilliscope patterns, which even displayed clipping when I was over-volume.

Oh, I also selected File/Device/Soundcard.

---

### Post by grey1beard on 2013-04-12
Thanks gordintoronto. I picked up your idea to check that I got sound recorder detecting the mic, which led me to switch mic channels in the sound settings !
Onwards and upwards - I now have the mic producing a trace in xoscope. Severely clipped, but I'll do some tests later with a simple oscillator to check what the settings on xoscope need to be. 
Seems strange that several of the drop down menus don't retain a 'bullet' on your chosen setting. Makes trial and error a bit tedious.
Noticed that in Sound Recorder, the setting 'Record from input' - Master seems to be the only choice, but as the trace was still visible in xoscope when I turned Sound Recorder off, I let that pass.

Thanks for your input,
John

---

