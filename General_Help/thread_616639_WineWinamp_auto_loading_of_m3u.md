---
title: "Wine/Winamp auto loading of m3u"
date: 2007-11-18
forum: General Help
---

### Post by klepto on 2007-11-18
Thanks to someone from the forums here i got uTorrent to automatically import torrent files due to a script that someone posted but for the life of me I can't get m3u's to automatically play in winamp through wine. Sure I can choose the m3u file and have it play it but I would like to have it automatically open through firefox. Any ideas?

Thanks

---

### Post by malfist on 2007-11-18
mplayer-plugin will allow you to play music and video in firefox, no wine needed.

edit: ktorrent is a lot like utorrent, and supports encryption too.

---

### Post by klepto on 2007-11-18
Well the m3u streams the video. I have mplayer and mplayerplugin but mplayer doesn't allow you to move the video forward or reverse. Vlc does but the picture becomes pixelated and winamp is the only app that does this perfectly as it was suggested.

---

### Post by klepto on 2007-11-18
If anyone ever wants to try this here is the script and I borrow part of it from whomever upload the uTorrent.sh script: 

#!/bin/sh
LANG=en_US.utf-8
LC_MESSAGES=en_US.utf-8
/usr/bin/wine "C:/Program Files/Winamp/winamp.exe"  `cat $1 | grep http` &


it works perfectly!

---

### Post by malfist on 2007-11-18
I would suggest you find other sources of video, if it pixilates or turns green when changing position, it wasn't encoded properly. Besides, just an opinion of mine, but I don't (and never have) trusted winamp.

---

