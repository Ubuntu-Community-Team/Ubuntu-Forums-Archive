---
title: "No idea how to use mencoder."
date: 2007-05-28
forum: General Help
---

### Post by omgDarkWillow on 2007-05-28
I'm trying to convert a video that I recorded with recordmydesktop from .ogg to .avi..but I can't for the life of me figure out how to work mencoder. I ran this in the terminal 
> mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi

 and I got this: 

> MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'input.ogg'
Failed to open input.ogg.
Cannot open file/device.

Any help?

Also, Totem and VLC won't play my .ogg file.

---

### Post by omgDarkWillow on 2007-05-29
Anyone?

---

### Post by zvacet on 2007-05-29
[https://help.ubuntu.com/community/MEncoder]("https://help.ubuntu.com/community/MEncoder")

---

### Post by omgDarkWillow on 2007-05-29
This time I ran this:

> mencoder </home/nate/Desktop/Stuff> -ovc lavc -o output_movie.avi

and got this:

> ============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Can it not convert OGG files?

---

### Post by fragos on 2007-05-29
The man pages for this are very extensive and confusing.  I've done some video conversion with "ffmpeg" of .flv to .mpg and .avi.  I don't have an video ogg files to try but you can try it.  Here's a command line with associated terminal response that worked for me.  Not quite what you asked but hopefully it will bring you closer to a solution.

fragos@Geo:~/Desktop$ ffmpeg -i Ghost_in_the_Shell_-_Trailer.flv -ab 56 -ar 22050 -b 500 -s 240x180 Ghost.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'Ghost_in_the_Shell_-_Trailer.flv':
  Duration: 00:01:52.9, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, mono
  Stream #0.1: Video: flv, yuv420p, 240x180, 29.97 fps(r)
Output #0, mpeg, to 'Ghost.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 240x180, q=2-31, 500 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame= 3368 q=2.0 Lsize=    7834kB time=112.3 bitrate= 571.2kbits/s    
video:6983kB audio:772kB global headers:0kB muxing overhead 1.025415%
fragos@Geo:~/Desktop$

---

### Post by ramjet_1953 on 2007-05-29
This software package may help:

[http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder](http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder)

However, it is sourcecode and you will need to compile and meet dependency requirements, unless you can find a deb package that someone has posted on the net.

Scrub the comment above. Here is a link for an Ubuntu download:

[email]t@b_tabencode_linux_ubuntu32_0703161351.tar.gz[/email]

Regards,
Roger :cool:

---

### Post by ramjet_1953 on 2007-05-29
Further to my previous post, it seems to work fine.

Just download the .tar.gz file and extract it.

A new folder called [COLOR="Blue"]filez[/COLOR] will be created.

just double click on the x-executable file [COLOR="Blue"]tabencode[/COLOR] and it should open.

If you want, just use [COLOR="Blue"]System>Preferences>Menu Layout[/COLOR] to create a menu item.

Regards,
Roger :cool:

---

### Post by omgDarkWillow on 2007-05-29
> **ramjet_1953 said:**
> This software package may help:

[http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder](http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder)

However, it is sourcecode and you will need to compile and meet dependency requirements, unless you can find a deb package that someone has posted on the net.

Scrub the comment above. Here is a link for an Ubuntu download:

[email]t@b_tabencode_linux_ubuntu32_0703161351.tar.gz[/email]

Regards,
Roger :cool:
That takes me to "Compose Message". My guess is it has something to do with the "@".

---

### Post by zvacet on 2007-05-30
[http://devel.zs4.org/tabencode_linux.html]("http://devel.zs4.org/tabencode_linux.html")

---

