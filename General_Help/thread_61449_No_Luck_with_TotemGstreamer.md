---
title: "No Luck with Totem/Gstreamer"
date: 2005-08-31
forum: General Help
---

### Post by damonkohler on 2005-08-31
I can't seem to get totem to play any video files. I've tried lots of videos including just normal mpg files. Previously I had just installed totem-xine and that worked out of the box. The only problem with that was that I didn't get any sound along with the videos. So, I figured I'd try the gstreamer version again. Sound works in general, I can get XMMS to play and such. Any ideas? Thanks...

---

### Post by AndrewB on 2005-08-31
go here: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) 

read...do..there's Wiki pages around as well

Peace

---

### Post by maril on 2005-08-31
i did apt-get install totem-gstreamer0.08 or something like that
i also tried apt-get install totem-xine

both of those allowed me to play divx/xvid.... i think

---

### Post by duan on 2005-09-01
I installed these, as well as totem-xine:

      gstreamer0.8-ffmpeg - newer MPEG support

      gstreamer0.8-plugins - Various other formats

And video is good on my machine but I had to install alsa to get proper audio sync in movies, with this walkthrough [http://www.ubuntuforums.org/archive/index.php/t-32063.htm](http://www.ubuntuforums.org/archive/index.php/t-32063.htm)

---

### Post by xyloc on 2005-09-12
I get another error message when using GStreamer/Totem:
"Resource Buisy or N/A"
I tried this with both Alsa and ESD, following the tips in the unoffical Ubuntu 5.04 Starter Guide.
MP3's play fine in Xmms, so there is no general sound issue.

When I install Totem/Xine instead, the player starts, my DivX movie starts, but no sound :-? 

My sound card is an onboard Ac'97 compatible ens1371.

---

