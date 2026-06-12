---
title: "real player"
date: 2005-09-05
forum: General Help
---

### Post by astronerd on 2005-09-05
Hi all, I just got some videos in real format and I would like to know what I need to play them in Xine or Totem if possible.  I thought that I had installed all the codecs, but apparently not.  Is there a package that I need, or is there something else that I can get via synaptic?  thanks, 
Charles

---

### Post by DJ_Max on 2005-09-05
I don't know about codecs for Totem. But there's always real.com or [https://player.helixcommunity.org/](https://player.helixcommunity.org/)

---

### Post by Harleen on 2005-09-05
Have you already installed the "w32codecs" package from the backports? It should enable mplayer and xine (and all players, that use these) to play files in real format - and many more.

---

### Post by astronerd on 2005-09-05
Yeah, I have the win32 packages installed.  I thought that it would work with that installed, but it still tells me that the plugin cant be found.  I dont really want to install helixplayer or the actual real player so I would like to figure out why or what to do with Xine/totem to get this working.  Any more ideas?

---

### Post by Harleen on 2005-09-06
Strange. Installing these codecs and xine was all I had to to to play real video files. Maybe your particular files require a newer codec than that one that is installed with the codec package?
If you can play certain avi or quicktime-files it would at least prove, that the windows codecs are used by xine.

---

### Post by astronerd on 2005-09-06
Got it working, just uninstalled the codecs and installed them again and it worked.  weird.  Thanks anyway!

---

