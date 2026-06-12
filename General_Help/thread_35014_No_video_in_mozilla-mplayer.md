---
title: "No video in mozilla-mplayer"
date: 2005-05-17
forum: General Help
---

### Post by agds on 2005-05-17
I was trying to watch the [FFVII Technical Demo](http://www.gamespot.com/ps3/rpg/finalfantasyvii/media.html?gcst=2stream_ps3ff7demo_e305.asx) at Gamespot.  The sniffer seems to detect my plug-in without any problems.  Unfortunately the playback has sound without video.  Instead there's a graphic that claims MPlayer is loading the file.  As much as I enjoy exercising my imagination, I'd prefer to see the movie as well as hear it.

Your help would be appreciated.

---

### Post by Xerampelinae on 2005-05-17
Strange, it works for me.

You might try changing the vo= line in /etc/mplayerplug-in.conf to something else.  I imagine it takes all the video output drivers that regular mplayer can take... so try:

vo=x11
or
vo=xv

Or see the mplayer man page for more options.  Hopefully that will work, but who knows...

---

### Post by w4e on 2005-05-17
Also, setting the video codec family to win32/vfw might do the trick (if installed of course).

---

### Post by agds on 2005-05-17
[QUOTE=Xerampelinae]You might try changing the vo= line in /etc/mplayerplug-in.conf to something else.[/QUOTE]
Actually my mplayerplug-in.conf includes both xv and x11 in the video output.  Here are the contents of the file.

```
#debug=0
#logfile=$HOME/mpp.log
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=256
#use-mimetypes=0
#enable-real=0
#enable-wm=1
#enable-qt=1
#enable-mpeg=1
#enable-ogg=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
```
I also discovered the opposite problem when playing the mov format, i.e. video without sound.  The mpg format works fine.

---

