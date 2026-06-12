---
title: "[SOLVED] swf to mp3"
date: 2007-08-21
forum: General Help
---

### Post by uroskriznar on 2007-08-21
Does anyone know if there is a swf (flash) to mp3 converter for Ubuntu? There seems to a lot these for Window.

---

### Post by scocrys on 2007-08-21
Have a look at this thread. I haven't tried it myself.
[http://www.linuxforums.org/forum/linux-applications/57545-swf-mpeg.html]("http://www.linuxforums.org/forum/linux-applications/57545-swf-mpeg.html")

---

### Post by uroskriznar on 2007-08-27
Well now I seem to have another problem. I did what u said but the program sais that the file is corrupt or something like that.

uros6@uros6-desktop:~$ ffmpeg -i Pedro Khima - Esfera.swf u.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Pedro: I/O error occured
Usually that means that input file is truncated and/or corrupted.

Then I tried the same thing in windows with a program and it sais that this is not a flash file???

But in ubuntu under properties and type it sais FLASH VIDEO, mime tipe: APPLICATION/X-FLASH-VIDEO.

I downloaded this video on you tube.

---

### Post by dwink1217 on 2007-08-27
well, im guessing you used keepvid or something LIKE that right? that it saves videos from online sites like that?

because those videos come in .flv, NOT .swf.

.flv is another type of flash video. you're looking for .flv to mpeg, not an .swf to mpeg.

---

### Post by uroskriznar on 2007-08-28
Thanks! I'll try to find this kind of software.

---

