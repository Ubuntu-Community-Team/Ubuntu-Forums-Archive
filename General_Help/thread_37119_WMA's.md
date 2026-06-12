---
title: "WMA's?"
date: 2005-05-25
forum: General Help
---

### Post by DeekoVB5 on 2005-05-25
I'm having trouble getting WMA's to work in ubuntu.  I have XMMS installed, but I can't get the WMA plugin to work - XMMS ignores it as if it isn't there.  Any help?

---

### Post by MrMojoRising on 2005-05-26
Check this page out...
[How to install mPlayer](http://ubuntuguide.org/#mplayer) 

mplayer offers tons of codecs preinstalled......including WMAsupport.
It's all I use.
There's even a plugin for Xmms which adds mplayer support, a little bit or forum searching and you'll find it.

---

### Post by bored2k on 2005-05-26
1. Try xine-ui (mplayer can sometimes be a b___)
2. > sudo apt-get install xmms
wget -c [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb

---

### Post by DeekoVB5 on 2005-05-26
[QUOTE=bored2k]1. Try xine-ui (mplayer can sometimes be a b___)
2.[/QUOTE]
 I've heard mplayer is a bitch....I'll try xine-ui, as for that second one, I'm using AMD64 so it won't load...

---

### Post by DeekoVB5 on 2005-05-26
[QUOTE=DeekoVB5]I've heard mplayer is a bitch....I'll try xine-ui, as for that second one, I'm using AMD64 so it won't load...[/QUOTE]
 Actually using mplayer right now, its working alright....setting it up to read my playlists and figuring out that everying must be done command line was a pain, but its runnin alright now.

---

### Post by jasplund on 2005-05-26
I use beep-media-player to play wma's. You need beep-input-wma first though. Check out [http://www.ubuntuforums.org/showthread.php?t=35272&highlight=beep+wma](http://www.ubuntuforums.org/showthread.php?t=35272&highlight=beep+wma)

---

### Post by Takis on 2005-05-26
What's the problem with XMMS? It worked for me first go.

---

### Post by lorap on 2005-05-27
hi friend!
try to install this codec - gstreamer0.8-ffmpeg
hope it'll solve your problem.
have a nice day.
pavel

---

