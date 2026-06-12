---
title: "mplayer plugin not working"
date: 2007-04-22
forum: General Help
---

### Post by gregalynch on 2007-04-22
I'm trying to get the embedded videos on the side of [this page]("http://www.chicagobears.com") to play.  I have mplayer installed as my video plugin (I uninstalled all the others).  Mplayer launches, and (when I set it to use HTTP) it connects, but it doesn't play the video.

---

### Post by luca.mg on 2007-04-23
I was having problems with mplayer too, after digging around this is my new mplayerplug-in.conf (it resides into the /.mplayer directory in your home dir) now everything works including the bears site! 

vo=x11
ao=alsa
cachesize=4130
cache-percent=33
dload-dir=/home/YOU_NAME_IT
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=0
rtsp-use-tcp=1
rtsp-use-http=1

---

### Post by gregalynch on 2007-04-24
I copied and pasted that using gedit to change the file, and I'm still having the same problem.  The screen where the video should be playing just shows a white screen with the mplayer logo and the word 'connected'.  Is there maybe some config setting I need to change?  (I've tried a lot of different combinations)

---

### Post by luca.mg on 2007-04-25
sorry to hear that, perhaps You miss the codec package(s).

---

