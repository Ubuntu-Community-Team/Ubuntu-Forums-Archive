---
title: "Only 1 sound source at any given time?"
date: 2008-04-29
forum: General Help
---

### Post by Deten on 2008-04-29
It seems that ubuntu 8.04 x86 wont let me play more than 1 source of sound at a time.  So if I have a music player open, and open a game or a video on firefox it wont play sound.

I have the 82801G Intel internal sound board in my laptop.  I remember having a similar problem in 7.10.

I followed the steps in the Comprehensive Sound Problems Guide
[http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound)
notably multiple sounds and multiple cards support section

I have rebuilt the latest drivers from the alsa website following the tutorial here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This did nothing to fix the problem



Thanks

---

### Post by Deten on 2008-04-30
deten@deten-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel CXD9872RD/K
Codec: Conexant ID 2bfa
deten@deten-laptop:~$

---

### Post by Zorael on 2008-04-30
Try 'aplay -l'.

Anyway, this depends on what **sound system** your application is using to output sound. Check in your media player settings to see if more than one is available.

For instance, in Amarok I can choose between pulseaudio, alsa, oss and file. File obviously outputs sound into a file (likely .wav). ALSA and OSS are both sound systems, and PulseAudio is sort of a sound system that plays atop of ALSA.

If you have PulseAudio installed (standard for Ubuntu but optional for Kubuntu), you always want to pick it when possible, else ALSA. OSS is old and deprecated, and it always hogs exclusive access.

---

### Post by Deten on 2008-04-30
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Also, I use movie player.  Its perfect for me.  In my windows days I used mediaplayer classic and "movie player" is close to it.

Is there a way to change mplayer to alsa if it is not currently?

---

### Post by Deten on 2008-04-30
By the way if you need help installing ventrilo through wine let me know, it works flawless for me.

---

### Post by jocko on 2008-04-30
> **Deten said:**
> Is there a way to change mplayer to alsa if it is not currently?

In the gui version (gmplayer), just right click somewhere in the video window to get the menu.
Click preferences, then the audio tab, where you can set which sound system to use.
For the no gui version, put this line:
```
ao=alsa
```
in the file ~/.mplayer/config

---

### Post by Deten on 2008-04-30
Thank you so much. 

It appears it naturally used something besides alsa, so I changed it, and now I can play multiple sounds while music is going! I am so freaking happy!

You deserve chocolate chip cookies.

---

### Post by gigabite on 2008-04-30
I am having the same problem. How do I change the sound system for Totem and Firefox?

---

### Post by jocko on 2008-04-30
If you set two different apps to use alsa, do you get sound from both at the same time?
If not, you need to configure alsa. This is how I did it:

First find the name of your sound card:
```
aplay -l
```Then have asoundconf make a default configuration for that card:
```
asoundconf set-default-card *name_of_your_card*
```where *name_of_your_card* is the name your card have according to "aplay -l".

Unfortunately the default behaviour of pulseaudio is to completely bypass any alsa settings, which means no other app will be able to use alsa if your card does not have hardware mixing. The easy "fix" is to set all apps to use pulseaudio (but I find this a bad fix, as it means you just accept that pulseaudio overrides your settings).

---

### Post by jocko on 2008-04-30
> **gigabite said:**
> I am having the same problem. How do I change the sound system for Totem and Firefox?

For totem and a lot of other gnome apps (that use gstreamer), open up gnome-sound-preferences and gstreamer-properties (if you can't find them in the menu, just type their names in a terminal to start them).
Change all options to the one you prefer (e.g. alsa).
Firefox uses alsa as far as I know (but if you have the flashsupport package installed, flash will use pulseaudio).

---

### Post by piratesmack on 2008-04-30
> **Deten said:**
> It seems that ubuntu 8.04 x86 wont let me play more than 1 source of sound at a time.  So if I have a music player open, and open a game or a video on firefox it wont play sound.

I have the 82801G Intel internal sound board in my laptop.  I remember having a similar problem in 7.10.

I followed the steps in the Comprehensive Sound Problems Guide
[http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound)
notably multiple sounds and multiple cards support section

I have rebuilt the latest drivers from the alsa website following the tutorial here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This did nothing to fix the problem



Thanks



```

sudo apt-get install libflashsupport

```

Will let fix the problem with sound in firefox while a music player is running. But it makes flashplayer a little unstable. I was having the same problem.

This bug doesn't seem to effect Ubuntu 64bit

---

### Post by jocko on 2008-04-30
> **piratesmack said:**
> This bug doesn't seem to effect Ubuntu 64bit

Which bug? That pulseaudio locks alsa, so you need to set all apps to use pulseaudio? Yes it affects all cards that doesn't have hardware mixing.
That flashsupport makes flashplayer unstable? Well, flashplayer has always been unstable for me, irregardless of using 32 or 64 bit, alsa, oss or pulseaudio, firefox crashes almost every time I start a youtube video after I have already seen another youtube video.
If it doesn't crash on the second video, it will for certain crash on the third or fourth.

---

### Post by gigabite on 2008-04-30
Thanks for the help in getting the audio problems corrected. Flash doesn't crash for me at all so I guess I'm lucky? I'm keeping my fingers crossed for sure.

---

### Post by Deten on 2008-10-30
I used alot of this info to get 8.10 working nicely as well :) THanks again for the long ago help haha

I am much more proficient with ubuntu now :)

---

