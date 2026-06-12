---
title: "VLC Media Player part2"
date: 2005-08-14
forum: General Help
---

### Post by blu.gecko on 2005-08-14
previously I tried to install vlc, I got frustrated and went with xine, well, I like vlc and have been using it on my wifes win32 machine, so I tried installing it, so far so good.

here is what I have done so far.

apt-get install gvlc

apt-get libdvdcss2

but my sound is missing. last time I tried this process,

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

and my audio was chopped and my video lagged.

so mabye Im overlooking something, I need some help.....

blu. :???:

---

### Post by Holdem on 2005-08-14
Try de-selecting Sound Server Startup
System-Preferences-Sound-Enabled Sound Server at Startup untick it.

---

### Post by blu.gecko on 2005-08-14
thanks man, fixed the sound, but is there any way to adjust the choppey video feed?

---

### Post by alanben1975 on 2005-09-11
have you enabled dma on your dvd player??

---

