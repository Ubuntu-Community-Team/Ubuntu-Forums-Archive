---
title: "[SOLVED] Amarok cannot play mp3s"
date: 2007-11-16
forum: General Help
---

### Post by skwishybug on 2007-11-16
I'm trying to use Amarok 1.4.7 (from the Repos) to play my mp3 files but I keep getting the following error:

No suitable demux plugin. This often means the file format is not supported

I can play the mp3 files in Exaile, Rhythm Box, pretty much any other program.

I can also play the .wma files without a problem in Amarok.

Any ideas?

---

### Post by gibbylinks on 2007-11-16
Sorry not help, but similar problem.

I can't playback MP3's and yet they play in Rhythmbox.

It keeps asking me to install MP3 support. I click yes, restart it and get the same message again.

I;ve tried reinstalling both Amarok and the Ubuntu-restricted-extras, with no joy.

Any help appreciated

---

### Post by geirha on 2007-11-16
Convert them to ogg ;P

I think you need the **libxine1-ffmpeg** package installed.

---

### Post by tech9 on 2007-11-16
or...
sudo apt-get install vlc

vlc media player plays mp3s

---

### Post by gibbylinks on 2007-11-16
> **geirha said:**
> Convert them to ogg ;P

I think you need the **libxine1-ffmpeg** package installed.

Give that man a Blue Peter badge. Right on the nail. I'm know listening to my MP3'S

:guitar:

---

### Post by Martje_001 on 2007-11-16
Please mark this thread as 'SOLVED'.

---

### Post by meindian523 on 2007-11-16
please marked thread as solved.....Thread tools-->Mark as Solved..

---

### Post by tech9 on 2007-11-16
> **gibbylinks said:**
> Give that man a Blue Peter badge. Right on the nail. I'm know listening to my MP3'S

:guitar:


seems like a lot of work converting all your MP3s to ogg :roll:

---

### Post by maybeway36 on 2007-11-16
libxine1-ffmpeg is also in kubuntu-restricted-extras, just FYI.

---

### Post by skwishybug on 2007-11-17
> **geirha said:**
> 
I think you need the **libxine1-ffmpeg** package installed.

That did it. Thanks for the help.

Thread solved.

---

