---
title: "[resolved] Totem-xine plays DVD w/ no sound"
date: 2004-11-23
forum: General Help
---

### Post by vontez on 2004-11-23
I just installed Ubuntu, and I removed Totem-gstreamer and installed Totem-xine.  Totem-xine plays my dvd video just fine, but there is no sound.  Gnome plays sounds outside of totem-xine, but I can't figure out how to get totem-xine to play sound.  Any suggestions?

I must say, I'm very impressed with Ubuntu's out of the box support of mostly every aspect of my system.  I'm used to compiling my own custom kernel just to get my wireless to work!

---

### Post by vontez on 2004-11-24
I got my DVD playback working correctly.  I ended up removing Totem-xine and installed MPlayer.

---

### Post by mullmuzzler on 2004-11-28
I have the same problem here. 
Any more suggestion other than mplayer or totem-gstreamer?

---

### Post by vontez on 2004-12-06
Sorry, I have no other solutions for you.  Have you tried installing mplayer?  It is a real nice player, and I haven't had any problems with it yet.

---

### Post by killerfish on 2004-12-07
I had the same issue and had to install more gstreamer plugins.  I forget which one does what you need, but there is a package to install them all.... Just search for gstreamer in synaptic...

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=mullmuzzler]I have the same problem here. 
Any more suggestion other than mplayer or totem-gstreamer?[/QUOTE]

sudo apt-get install gstreamer0.8-plugins

---

