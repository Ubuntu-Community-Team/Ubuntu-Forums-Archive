---
title: "ffmpeg not working"
date: 2005-10-16
forum: General Help
---

### Post by jtonk on 2005-10-16
hi everybody,

In my last distro (debian unstable) I managed to get ffmpeg working with psp support to encode movies for my clie in mp4 format. Now in Hoary and Breezy I am unable to get this working. Whenever I try to encode a movie:

ffmpeg -i sourcemovie.avi -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00001.MP4

I get the message:

ffmpeg version CVS, build 4759, Copyright (c) 2000-2004 Fabrice Bellard
configuration:
built on Jul 28 2005 23:27:56, gcc: 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Input #0, avi, from 'sourcemovie.avi':
Duration: 00:42:04.8, start: 0.000000, bitrate: 1164 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 608x336, 23.98 fps
Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Output #0, psp, to 'M4V00001.MP4':
Stream #0.0: Video: mpeg4, yuv420p, 320x240, 14.98 fps, q=2-31, 768 kb/s
Stream #0.1: Audio: 0x0000, 24000 Hz, stereo, 32 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
[mpeg4 @ 0x8387d14]removing common factors from framerate
Unsupported codec for output stream #0.1


I get this with any movie, I have no idea what is means. Movie playback works fine, reencoding doesn't work in ANY format.

I tried compiling ffmpeg from scratch but that failed as wel.

Any help would be appreciated.

regards,

Jasper

---

### Post by placide on 2006-03-10
Hi!
I had the same problem.I think there is some problem with the compilation of the package, so I compiled it myself.

You can get the package here:
[http://ffmpeg.sourceforge.net/download.php](http://ffmpeg.sourceforge.net/download.php)

then I use these configure parameters (feel free to adjust to your needs!!!)

--------------------------------------
./configure --prefix=/usr --enable-libogg --enable-vorbis --enable-theora --enable-faad --enable-faac --enable-a52 --enable-gpl --enable-mp3lame
make
sudo make install
-------------------------------------

note: "--enable-x264" gave me an error?!?

I also found some debian packages here:
[http://202.205.109.38/debian-uo/dists/sid/marillat/pool/](http://202.205.109.38/debian-uo/dists/sid/marillat/pool/)
but didn't use them

enjoy!!!

:mrgreen:

---

