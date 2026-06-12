---
title: "Extracting music from .swf files?"
date: 2008-02-06
forum: General Help
---

### Post by Muscar on 2008-02-06
Is there a way to extract the music from a .swf file?

here is the site that i want the music from:
[http://pixel.customize.org/](http://pixel.customize.org/)

---

### Post by Muscar on 2008-02-06
Hello!?

---

### Post by Muscar on 2008-02-06
sorry

---

### Post by y-lee on 2008-02-06
I use audacity to record the audio of any video. It is a complex tool and I'm no master of it since i rarely do it. So I can't offer to help ya learn to use it.

also ya can try

 ```
mplayer -dumpaudio "whatever.swf" -dumpfile whatever.mp3
```

there is alot of ways of doing this, even some online tools tho I can't find them right now. I would suggest google. Many software tools tho most if not all are windows apps.

and btw be patient I help alot of people here o rtry to and so do many others. things take time .

---

### Post by Keith Hedger on 2008-02-06
Use:```
ffmpeg -i /path/to/flash/file -ac 2 -ar 48000 -ab 128 /path/to/outfile.wav
```
and to convert to mp3```
lame -m j -h -b 128 --resample 48 /path/to/outfile.wav ./path/to/mp3file.mp3
```
Hope this helps

---

### Post by cdaringe on 2008-02-06
> **Muscar said:**
> Ok, just don't care thenreally man? don't bite the hand that feeds ya

---

### Post by Muscar on 2008-02-06
sorry for being an ashole, but i've been trying to about 3 days now and i really want the music, well i've tried al of the things posted here and no-one worked

here is the error from Keith Hedger way:

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
/home/marcus/dekstop/site.swf: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by Keith Hedger on 2008-02-06
Sorry that didnt work (ut works fine for swf from youtube) what exactly is the url of the swf you are trying to download? I had a look at the site and the music seems to be in a seperate file at [http://pixel.customize.org/freshcut.mp3](http://pixel.customize.org/freshcut.mp3) what is the legal position here? if this material is copyrighted then you cant touch it

---

### Post by Muscar on 2008-02-06
i fixed it, thanks

---

### Post by Keith Hedger on 2008-02-06
Just for other peoples info what was the fix? and mark the thread as SOLVED

---

