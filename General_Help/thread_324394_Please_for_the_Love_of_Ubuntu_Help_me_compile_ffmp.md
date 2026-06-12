---
title: "Please for the Love of Ubuntu: Help me compile ffmpeg with AAC support"
date: 2006-12-23
forum: General Help
---

### Post by kd7swh on 2006-12-23
Please get me an easy howto on compiling ffmpeg with different codec supports!

I try to compile, and it can't find any of the libraries, or codecs that I have installed.

lame, xvid, faac, none of them.

please help me!!!

](*,)

I don't even care if it is easy or not.... :(

---

### Post by hanzomon4 on 2006-12-23
> **kd7swh said:**
> Please get me an easy howto on compiling ffmpeg with different codec supports!

I try to compile, and it can't find any of the libraries, or codecs that I have installed.

lame, xvid, faac, none of them.

please help me!!!

](*,)

I don't even care if it is easy or not.... :(

Here ya go:```
./configure  --enable-mp3lame --enable-libogg --enable-vorbis --enable-faad --enable-dts --enable-pp --disable-debug --enable-pthreads --enable-dc1394 --enable-gpl --enable-faac --enable-libgsm --enable-xvid --enable-a52
```

---

### Post by kd7swh on 2006-12-23
I got this in return:


ERROR: LAME not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-devel@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

---

### Post by hanzomon4 on 2006-12-23
Just install liblame-dev ```
sudo aptitude install liblame-dev
```

---

### Post by taurus on 2006-12-23
Make sure you have these two lines in ~/.mplayer/gui.conf!!!

```

v_vfm = "ffmpeg"
a_afm = "ffmpeg"

```
Otherwise, run **gmplayer** from a terminal and then 

Preferences -> Codecs & demuxer:

Video codec family:  FFmpeg.....
Audio codec family:  FFmpeg.....

---

### Post by kd7swh on 2006-12-23
aac decoding is fine, I need a working aac encoder\library for ffmpeg

---

### Post by kd7swh on 2006-12-23
ffmpeg is compiling now and claims to have faac, faad, mp3lame, and vorbis enabled but only vorbis works for audio encoding.

mp3lame and faac say - unknown codec

---

### Post by hanzomon4 on 2006-12-24
This is the output I get ```
./configure  --enable-mp3lame --enable-libogg --enable-vorbis 
--enable-faad --enable-dts --enable-pp --disable-debug --enable-pthreads --enable-dc1394 
--enable-gpl --enable-faac --enable-libgsm --enable-xvid --enable-a52
install prefix   /usr/local
source path      /home/hanzomon4/.development/svn/ffmpeg
C compiler       gcc
make             make
CPU              x86 (generic)
big-endian       no
inttypes.h       yes
broken inttypes.h no
MMX enabled      yes
Vector Builtins  yes
3DNow! Builtins  yes
gprof enabled    no
zlib enabled     yes
libgsm enabled   yes
mp3lame enabled  yes
libogg enabled   yes
Vorbis enabled   yes
FAAD enabled     yes
faadbin enabled  no
FAAC enabled     yes
XviD enabled     yes
x264 enabled     no
a52 support      yes
a52 dlopened     no
DTS support      yes
pp support       yes
debug symbols    no
strip symbols    yes
optimize         yes
static           yes
shared           no
video hooking    yes
SDL support      yes
Imlib2 support   yes
FreeType support yes
Sun medialib support no
pthreads support yes
AMR-NB float support no
AMR-NB fixed support no
AMR-WB float support no
AMR-WB IF2 support no
network support      yes
IPv6 support         yes
License: GPL
Creating config.mak and config.h...

```

---

### Post by kd7swh on 2006-12-24
Ok, I got it now. I had to compile from the cvs sources and not svn among other things.
after playing with dev-libs and this post [http://www.ubuntuforums.org/showthread.php?t=114946](http://www.ubuntuforums.org/showthread.php?t=114946) 
I finally got it to start encoding! :)

---

### Post by hanzomon4 on 2006-12-24
I found the howto I used to compile ffmpeg, I'll post the relevant parts: 
[quote=endersshadow's]
```
sudo apt-get build-dep ffmpeg
```
```
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev
```

```
./configure --enable-gpl --enable-pp --enable-vorbis \
	--enable-libogg --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
```
```
make
```
```
sudo checkinstall -D make install
```[/quote]
[B]
EDIT:[/B]lol!!!! I was late by minutes

---

### Post by unikuser on 2007-09-28
For those who want to get ffmpeg compiled with all codecs without compiling, this site [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) is handy. You can get deb for ffmpeg here.

---

