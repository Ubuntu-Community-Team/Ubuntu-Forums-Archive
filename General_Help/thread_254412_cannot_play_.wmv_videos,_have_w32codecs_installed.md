---
title: "cannot play .wmv videos, have w32codecs installed"
date: 2006-09-09
forum: General Help
---

### Post by Polygon on 2006-09-09
i downloaded this video (specifically the hl2 ep2 gameplay trailer #5) and wanted to watch it in linux. but, in totem the player says that:

 it could not play the file (You do not have a decoder installed to handle this file. You might need to install the necessary plugins)

ive checked and i DO have w32codecs installed

in mplayer it does play but i get an error every .5 seconds about it not being able to find "simple control 'PCM',0"

and with firefox using the mplayer plugin it plays (laggy) for a few seconds and then the audio drops out and doesnt start again.

suggestions?

---

### Post by Polygon on 2006-09-10
bump

---

### Post by mostwanted on 2006-09-10
If you're using GStreamer, you need pitfdll (there is a Gstreamer 0.10 and 0.8 version, you probably need the latest one).

---

### Post by Polygon on 2006-09-10
i tried installing the .10 version ( i had .8 already installed) and it didnt do anything. in totem it says that the subclass didnt specify the output size and i get the same error in mplayer.

---

### Post by Albi on 2006-09-10
open it with kaffeine

---

### Post by Polygon on 2006-09-11
that wont solve my problem and i dont use kde, i use gnome.

---

### Post by BenTyreman on 2006-09-11
A guaranteed way of playing the video is to download mplayer, and manually install the latest codecs from the mplayer website. I've done this, and I haven't come across anything I can't play. Perhaps the error messages you are getting off mplayer are due to incorrect configuration? I use the alsa output for audio and gl for video.

---

### Post by Cynical on 2006-09-11
```

sudo apt-get install totem-xine totem-xine-firefox-plugin

```

That should let you watch it from whatever website you are getting it from as well.

---

### Post by bobex on 2006-09-12
I agree with mplayer before, I think mplayer is the best video audio player in linux, it is able to do almost anything, if you use totem-xine and in some case you got video that is the audio and video not scyncronized, you can'r do anything, but in mplayer you can adjust it. The best to install mplayer in download it in their site, and compile it yourself, don't forget to download w32codecs to. I've been using mplayer for a year and thereis nothing i cannot play, even the 3gp video. thanks.

---

### Post by Polygon on 2006-09-12
w32 codecs is installed

i reinstalled all versions of mplayer on my system, mplayer -386 , mplayer-k7, and just regular mplayer. 

I downloaded the lasest codecs and put them in /usr/lib/codecs



I guess the problem is with mplayer itself.. cause with my sound settings set to alsa, i get the "could not find simple control PCM 0" error every .5 seconds when i play ANY video with mplayer. But then when i switch sound to like esd, the sound starts lagging and skips to keep up or something

my sound is set to alsa and my video is set to gl.... what could be the problem

---

### Post by BenTyreman on 2006-09-12
Think I've found the solution. If you go into gmplayer preferences, then the audio tab. Select alsa, then configure driver. Experiment with mixer channel. Mine is currently set to driver default. PCM,0 is missing, but there does exist PCM and PCM,1. Perhaps one of these will make it work.

---

### Post by Polygon on 2006-09-14
if i switch the mixer channel to pcm or pcm 1, all it does is replace PCM 0 with PCM  or whatever in the error message

i get the same thing i do like "master" or whatever

so.. this leads me to that this is a problem with alsa maybe... because i just noticed .MOV and .AVI files have the same error...

---

