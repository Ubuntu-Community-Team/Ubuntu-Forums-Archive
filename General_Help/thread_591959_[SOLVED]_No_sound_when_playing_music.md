---
title: "[SOLVED] No sound when playing music"
date: 2007-10-25
forum: General Help
---

### Post by sixstorm on 2007-10-25
All of my sounds work, including startup sounds and sounds in Firefox (videos from YouTube and such).  The only thing that doesn't work is the sound when playing music in any music player.  Neither Banshee nor Rhythmbox works.  The file is playing but no sound.  When I double-click a MP3, Movie Player opens but it crashes.  Any help?

My sound chip is the Intel HDA ICH8.

Also, all GStreamer plugins are installed.  I'm also running Gutsy x64.

---

### Post by zvacet on 2007-10-26
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by sixstorm on 2007-10-26
> **zvacet said:**
> [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

No luck, even though I already had all codecs installed already.  It was working before I did a reinstall.

---

### Post by sixstorm on 2007-10-26
I finally found out the "problem".  My sound was configured correctly, I just didn't have Ubuntu directing to the right sound source.  Under System-Pref-Sounds, Ubuntu set my sound playback to "Coxanent Digital".  All I needed to do was change it to "ALSA" and everything works fine now!  

Hopes this help anybody else having issues.

---

