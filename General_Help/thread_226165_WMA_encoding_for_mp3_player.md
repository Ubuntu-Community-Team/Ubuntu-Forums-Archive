---
title: "WMA encoding for mp3 player"
date: 2006-07-30
forum: General Help
---

### Post by tjb891 on 2006-07-30
i know what your thinking, Why would i want to use inferior WMAs when I can use ogg or mp3? Well my mp3 player can hold 420 wma songs but only 240 mp3 songs, on top of that all my mp3s are encoded at very high bitrates (around 330 kbps). Since the encoder Microsoft gives out for windows is slow, bloaty, confusing, intrusive, ect,ect, is there a better free software alternative?

---

### Post by adamkane on 2006-07-30
Use the audio-convert script.

---

### Post by RAOF on 2006-07-30
Not as far as I'm aware.  I don't think any OSS developer cares enough to implement a WMA encoder.

Why don't you just transcode from your high bitrate MP3s to a lower bitrate mp3?  The 420 vs 240 song limit is surely due to size, not any other factor, so if you encode your mp3s to be the same size as the wma files...

---

### Post by dimeotane on 2006-12-03
Yup, using wine you can.  I tried a few dozen windows WMA encoders tonight and I did manage to get one to work. 

Download and install dbpoweramp plus the wmav2 codec: (the wma9 didn't seem to work under wine, but v2 did)

[http://www.dbpoweramp.com/bin/dMC-r10.exe](http://www.dbpoweramp.com/bin/dMC-r10.exe)
[http://www.dbpoweramp.com/codecs/dBpowerAMP-codec-wmav2.exe](http://www.dbpoweramp.com/codecs/dBpowerAMP-codec-wmav2.exe)



What I was needing was to encode WMA files to put on my Olympus digital voice recorder.  It can play mp3 files, but for some reason I couldn't get .spx files to convert into mp3 to work on the player.  By converting to .wma using this setup, my player could then read the files!

---

