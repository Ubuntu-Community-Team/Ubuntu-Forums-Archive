---
title: "Sporadic sound dropping out in mplayer - gutsy"
date: 2008-01-06
forum: General Help
---

### Post by JohnPhys on 2008-01-06
This happened recently (past two weeks or so), and I haven't been able to track down exactly what caused it, so I'm wondering if people here can help.

With mplayer, when watching various movies the audio will drop out every once in a while for a short while (half a second or so).  

I can't find any pattern to this (network or cpu usage spikes).  I have tried reinstalling the w32codecs, mplayer, and ffmpeg packages.  No luck.  It also happens when using either the -afm mp3 or -afm ffmpeg options to set the audio format.

EDIT:  I should add, movies seem to play fine in totem.  I also installed a package that removed libavformat0d, libavcodec0d, libpostproc0d (before I noticed the dropped sound).  I cannot seem to reinstall these three packages, but I do have libavformat1d, libavcodec1d, and libpostproc1d (medibuntu packages) installed.

Any ideas?

--John

---

