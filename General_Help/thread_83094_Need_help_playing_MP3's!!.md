---
title: "Need help playing MP3's!!"
date: 2005-10-27
forum: General Help
---

### Post by Spunkyboy2812 on 2005-10-27
Hey, i just got limewire up and running, downloaded a few songs, but they wont play.  Well it appears that they're playing, but theres no sound.  CD's work, and all other computer sounds work, but when i try to play an MP3 with either VLC or Limewire it looks like its playing but theres no sound.  Any ideas?? I checked my sound card driver and everything, its only when i try to play mp3's.

---

### Post by Riverside on 2005-10-27
[QUOTE=Spunkyboy2812]Hey, i just got limewire up and running, downloaded a few songs, but they wont play.  Well it appears that they're playing, but theres no sound.  CD's work, and all other computer sounds work, but when i try to play an MP3 with either VLC or Limewire it looks like its playing but theres no sound.  Any ideas?? I checked my sound card driver and everything, its only when i try to play mp3's.[/QUOTE]Some folks have trouble with this.  Using Breezy, all I had to do was:

sudo apt-get install xmms

And the xmms application would then play MP3 files straight away.  Others though have reported having to do all kinds of weird and wonderful things involving codecs etc to enable MP3 playing using xmms (and other applications).

---

### Post by Spunkyboy2812 on 2005-10-27
Hey thnx, but still no luck

---

### Post by x2l2 on 2005-10-27
same problem here

i try to install  gstreamer-ffmpeg and it works :-)

---

### Post by badboyz107 on 2005-10-28
try all this crap if you cant get it goin...I have had the same issues and finally got it all nailed down thanks to a lot of help!

---

### Post by jeffreyvergara.NET on 2005-10-28
try using automatix and install multimedia codecs. You can also try installing aMarok if you want a player that is similar to WMP9/10

---

### Post by doclivingston on 2005-10-28
[QUOTE=x2l2]i try to install  gstreamer-ffmpeg and it works :-)[/QUOTE]

I'd actually use gstreamer-mad, because gstreamer-ffmpeg can't read ID3 tags properly.

---

