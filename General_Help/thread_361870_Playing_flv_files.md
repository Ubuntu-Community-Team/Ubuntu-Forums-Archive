---
title: "Playing flv files"
date: 2007-02-14
forum: General Help
---

### Post by j5tixc on 2007-02-14
Hello, is there any way to play flv files that you keep getting the```
[flv @ 0x85f5200]Unsupported video codec (4)
```error with?

---

### Post by drivel on 2007-02-14
Sure that you have installed the codec?

---

### Post by j5tixc on 2007-02-14
Yes I have. Someone earlier said something about the VP6 codec and flash 8 video files being impossible to play in Linux.

---

### Post by fragos on 2007-02-15
Display being able to play FLVs in Firefox I discovered a standalone approach.  The answer I found was to convert the FLV with ffmpeg.  An example follows.  You need only enter the ffmpeg command as below and the rest is just the command being chatty.  In this example I convert Ghost_in_the_Shell_-_Trailer.flv into Ghost.mpg.  You may then use mplayer or whatever to view the MPG.

*** Successful conversion of Ghost in the Shell to mpeg ***
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

### Post by j5tixc on 2007-03-09
> **fragos said:**
> Display being able to play FLVs in Firefox I discovered a standalone approach.  The answer I found was to convert the FLV with ffmpeg.  An example follows.  You need only enter the ffmpeg command as below and the rest is just the command being chatty.  In this example I convert Ghost_in_the_Shell_-_Trailer.flv into Ghost.mpg.  You may then use mplayer or whatever to view the MPG.

*** Successful conversion of Ghost in the Shell to mpeg ***
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

Yes I've heard of converting files like that. Unfortunately I just get the same error message:
```
[flv @ 0x85f5200]Unsupported video codec (4)
```
Like I said, it seems like flash 8 files specifically are difficult to play.

---

### Post by fragos on 2007-03-10
I've had good luch with the Flash 9 player in Firefox.   I've gone out of my way to load every codec I could find.  Perhaps the one you're missing is available.  I'd be sure to load the MS codecs.  Also mplayer brings along a large set of codecs with it.

---

### Post by j5tixc on 2007-03-10
> **fragos said:**
> I've had good luch with the Flash 9 player in Firefox.   I've gone out of my way to load every codec I could find.  Perhaps the one you're missing is available.  I'd be sure to load the MS codecs.  Also mplayer brings along a large set of codecs with it.

Yes but it seems like Flash 8 flv-files are the ones giving me trouble. Apparently they use the VP6 codec. I mean I get some flv-files to play, but just not "flash 8" ones. I've been searching the Internet and haven't found a solution to the problem.


[http://www.ubuntuforums.org/showthread.php?t=216787](http://www.ubuntuforums.org/showthread.php?t=216787)
> **whatever said:**
> you can only play/reencode flv files which use the h263 codec.
those "flash 8 required"-movies use the vp6 codec and are not (yet) supported bei mplayer/mencoder.

---

### Post by SurR3AL on 2007-03-10
doesnt vlc play .flv?

---

### Post by j5tixc on 2007-03-10
> **SurR3AL said:**
> doesnt vlc play .flv?

I can play some flash files, both in mplater, vlc etc. But flash 8 VP6 encoded files I can't get to play in anything.

---

### Post by SurR3AL on 2007-03-10
oh...have u installed flash 9? check [here]("http://www.psychocats.net/ubuntu/flash")

---

### Post by fragos on 2007-03-10
> **j5tixc said:**
> Yes but it seems like Flash 8 flv-files are the ones giving me trouble. Apparently they use the VP6 codec. I mean I get some flv-files to play, but just not "flash 8" ones. I've been searching the Internet and haven't found a solution to the problem.


[http://www.ubuntuforums.org/showthread.php?t=216787](http://www.ubuntuforums.org/showthread.php?t=216787)

Hopefully a VP6 codec will be available soon.  For maximum browser support most sites save all flash as Flash 7.  I assume VP6 is another proprietary Microsoft gift to the world that only serves to eliminate anything but IE and Windows.  Another dumb trick that has been used is to put Flash in an ActiveX envelope.

---

### Post by j5tixc on 2007-03-10
> **SurR3AL said:**
> oh...have u installed flash 9? check [here]("http://www.psychocats.net/ubuntu/flash")

Yes I have. I'm having trouble with flv-files not swf-files. Like I said, I can't get flash 8 video files with the VP6 codec to play.

> **fragos said:**
> Hopefully a VP6 codec will be available soon.  For maximum browser support most sites save all flash as Flash 7.  I assume VP6 is another proprietary Microsoft gift to the world that only serves to eliminate anything but IE and Windows.  Another dumb trick that has been used is to put Flash in an ActiveX envelope.

Ok, like you said, hopefully VP6 support is coming.

---

### Post by strabes on 2007-03-10
You can convert .flv files to .avi with this bash script:

[http://applications.linux.com/article.pl?sid=06/08/22/2121258&tid=39](http://applications.linux.com/article.pl?sid=06/08/22/2121258&tid=39)

It's pretty easy.

---

### Post by j5tixc on 2007-03-10
> **strabes said:**
> You can convert .flv files to .avi with this bash script:

[http://applications.linux.com/article.pl?sid=06/08/22/2121258&tid=39](http://applications.linux.com/article.pl?sid=06/08/22/2121258&tid=39)

It's pretty easy.

Well, like I said before, that doesn't seem to work with flash 8 VP6 encoded files.

[http://www.ubuntuforums.org/showpost.php?p=2276550&postcount=7](http://www.ubuntuforums.org/showpost.php?p=2276550&postcount=7)
[http://www.ubuntuforums.org/showpost.php?p=1262027&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1262027&postcount=3)
> **whatever said:**
> you can only play/reencode flv files which use the h263 codec.
those "flash 8 required"-movies use the vp6 codec and are not (yet) supported bei mplayer/mencoder.

---

### Post by phenest on 2007-03-11
I'm getting the same error. What is the solution (if any)? I have some flv files downloaded from [www.ifilm.com]("http://www.ifilm.com")

---

### Post by SurR3AL on 2007-03-11
i dont know if this will work, but maybe you can convert the flv's to some other format? i found [this]("http://www.kde-apps.org/content/show.php?content=53610") software.

---

### Post by j5tixc on 2007-03-11
> **phenest said:**
> I'm getting the same error. What is the solution (if any)? I have some flv files downloaded from [www.ifilm.com]("http://www.ifilm.com")
Good question, I haven't found a way yet myself. But since you can watch the videos on the page they're on like ifilm, it feels like there should be an easy way.

> **SurR3AL said:**
> i dont know if this will work, but maybe you can convert the flv's to some other format? i found [this]("http://www.kde-apps.org/content/show.php?content=53610") software.

It seems like it just uses mencoder which can't do that as I posted above.


Here's an example file if anyone wants to try:
[http://rapidshare.com/files/20530394/2825115_300.flv.html](http://rapidshare.com/files/20530394/2825115_300.flv.html)

---

### Post by panch0 on 2007-03-12
A silly question: you do have libavcodec and libavformat installed, don't you?

I'm asking since I see this on MPlayer home page:

> MPlayer 1.0rc1 released

...The highlights of this release are native VC-1/WMV3, On2 VP5 and VP62 (used in some Flash video files) decoding...

So the latest official MPlayer (released back in October) is supposed to decode that VP6 stuff natively, and with w32codecs it was supposed to work even before then.

---

### Post by j5tixc on 2007-03-12
> **panch0 said:**
> A silly question: you do have libavcodec and libavformat installed, don't you?

I'm asking since I see this on MPlayer home page:



So the latest official MPlayer (released back in October) is supposed to decode that VP6 stuff natively, and with w32codecs it was supposed to work even before then.

That's interesting, I do have ffmpeg, mplayer and w32codecs. But only mplayer "MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8". Can you play the file I posted above successfully?

---

### Post by fragos on 2007-03-12
I went to that site but since I had to pay to download a file of that size I choose not to.

---

### Post by j5tixc on 2007-03-12
> **fragos said:**
> I went to that site but since I had to pay to download a file of that size I choose not to.

You don't have to pay, just click "Free".

Here's an alternative link:
[http://download.yousendit.com/D80D0EB93087BE9A](http://download.yousendit.com/D80D0EB93087BE9A)

---

### Post by fragos on 2007-03-12
Downloaded and I don't have the codec either.  ffmpeg and totem both failed on missing codec.  I wouldn't know where to look past what I've already found.  Good luck.

Edit: tried mplayer just in case but still got an error message.

---

### Post by panch0 on 2007-03-13
Do you have libavcodec and libavformat installed? MPlayer needs those to play FLV.

If you have them and it still doesn't work, please post the output you get from MPlayer.

---

### Post by fragos on 2007-03-13
LAVF_header: av_find_stream_info() failed

---

### Post by j5tixc on 2007-03-13
> **panch0 said:**
> Do you have libavcodec and libavformat installed? MPlayer needs those to play FLV.

If you have them and it still doesn't work, please post the output you get from MPlayer.
Also my output is basically in the first post, here's all of it:
```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing 2825115_300.flv.
libavformat file format detected.
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
LAVF_header: av_find_stream_info() failed
libavformat file format detected.
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
[flv @ 0x85f5200]Unsupported video codec (4)
LAVF_header: av_find_stream_info() failed


Exiting... (End of file)

```
(Removed thousands of "[flv @ 0x85f5200]Unsupported video codec (4)".)

---

### Post by panch0 on 2007-03-14
> MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8

Your MPlayer is very old, you need 1.0rc1. Try this one:

[http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-nogui_1.0~rc1-0ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-nogui_1.0~rc1-0ubuntu7_i386.deb)

if you are on i386, else find the right one for you.

---

### Post by j5tixc on 2007-03-14
> **panch0 said:**
> Your MPlayer is very old, you need 1.0rc1. Try this one:

[http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-nogui_1.0~rc1-0ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-nogui_1.0~rc1-0ubuntu7_i386.deb)

if you are on i386, else find the right one for you.

That's odd, I thought I had tried it with a newer version, maybe I was messing with uninstalling and installing ffmpeg at that time. Well anyways, now I can play the files I wanted. :) So thanks to everyone who helped!

---

