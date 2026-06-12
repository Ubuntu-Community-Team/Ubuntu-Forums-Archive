---
title: "Help with MP4 and ffmpeg"
date: 2006-10-10
forum: General Help
---

### Post by super breadfish on 2006-10-10
I've got some videos I want to convert to mp4. I've tried ffmpeg which I've used before with other formats but it doesn't work with mp4. It just gives the message "unsupported codec for output stream". 

As far as I know I have the right codecs, I can play mp4s. Or is ffmpeg just not that great with mp4?

I'd appreciate any help you might have.

---

### Post by moore.bryan on 2006-10-10
*depending on the format of the original video, you could get one of the command-line tools (e.g. [avi2mp4]("http://kev.coolcavemen.com/static/scripts/avi2mp4-2006_04_09.py"))...*

---

### Post by super breadfish on 2006-10-12
How do I use that? I've downloaded it but I don't know what to do with it. Sorry if it's a bit noobish.

---

### Post by moore.bryan on 2006-10-12
*not noobish, no worries.  with python installed (use synaptic to get it if you need to).  i've never used it, but you should just copy it into the folder where the files live you need to convert and then run it via ```
sudo python avi2mp4-2006_04_09.py
``` if that doesn't work, let me know what error message it gives you and we can try to figure this out. *

---

### Post by super breadfish on 2006-10-12
I got it working, and it converted it. The sound doesn't work though :(

---

### Post by moore.bryan on 2006-10-12
*no sound at all?  that's a little weird... try deleting the new mp4's and reconvert the avi's...*

---

### Post by super breadfish on 2006-10-12
No, there is still no sound. 

I'll try something different.

---

### Post by moore.bryan on 2006-10-12
*is there any particular reason why you want to convert them; after all, both are lossy...*

---

### Post by lawina on 2006-10-12
I installed Automatix and checked codecs and mplayer and MP4 just works.

---

### Post by super breadfish on 2006-10-13
My phone plays MP4 videos, and I had a couple of short clips I wanted to put on that.

I've not use Automatix before. I'll look into it though.

---

### Post by moore.bryan on 2006-10-13
> **lawina said:**
> I installed Automatix and checked codecs and mplayer and MP4 just works.
*mp4 works with mplayer no probs, but afaik it doesn't covert.*

---

### Post by super breadfish on 2006-10-13
I think I'll have to give up on this one. After some searching for alternatives I installed mencoder but couldn't follow the documentation at all. One site suggested compiling ffmpeg yourself, but I can't find any instructions on how to do that either.

I think I had a Windows program that did mp4 somewhere, I'll try that on XP.

---

### Post by moore.bryan on 2006-10-13
> **super breadfish said:**
> I think I'll have to give up on this one. After some searching for alternatives I installed mencoder but couldn't follow the documentation at all. One site suggested compiling ffmpeg yourself, but I can't find any instructions on how to do that either.

I think I had a Windows program that did mp4 somewhere, I'll try that on XP.
[I]compiling from source is usually a cake-walk, but it's a little more complicated with ffmpeg since its subverted... if you want to try it out, this should work:
```
sudo aptitude install --with-recommends subversion
svn checkout svn://svn.mplayerhq.hu/ffmeg/trunk ffmpeg
cd ffmpeg (or whatever the folder created is)
./compile
make
sudo make install
```if you do decide to compile, let me know how it works out for you...
[/I]

---

### Post by super breadfish on 2006-10-14
The first two parts work, and I change to the ffmpeg folder. But then I get 

bash: ./compile: No such file or directory

---

### Post by moore.bryan on 2006-10-14
*what IS in the dir?*

---

### Post by super breadfish on 2006-10-14
berrno.h
build_avopt
Changelog
clean-diff
cmdutils.c
cmdutils.h
common.mak
configure
COPYING
CREDITS
cws2fws.c
doc
Doxyfile
ffinstall.nsi
ffmpeg.c
ffplay.c
ffserver.c
ffserver.h
INSTALL
libavcodec
libavformat
libavutil
libpostproc
libswscale
MAINTAINERS
Makefile
output_example.c
pktdumper.c
qt-faststart.c
README
tests
unwrap-diff
version.sh
vhook
xvmc_render.h

---

### Post by moore.bryan on 2006-10-14
*sorry, that was my fault... it the code should be "./configure" not "./compile."  what a huge difference the right word makes...*

---

### Post by super breadfish on 2006-10-15
I got it installed ok, but I still get the same problem. I managed to get an MP4 with no sound (though VLC Media Player plays it fine) after some reading, but that's it.

---

### Post by moore.bryan on 2006-10-15
*sorry, super... i'm not sure i have the knowledge to take this any further... have you tried specifying a different sound system (i.e. if you're using alsa, changing to oss).  i don't see why that would matter, but none of this makes sense any way...*

---

### Post by super breadfish on 2006-10-16
Hey, don't worry. I tried the ffmpeg deb from [http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/) after seeing it mentioned in another topic and it works fine.

I think it was because I hadn't set up aac support in the others, because the working one I have now uses aac for audio in mp4. 

Thanks for all your help :D

---

### Post by moore.bryan on 2006-10-16
*aac support makes sense now... i'm not sure why i didn't think of it.  just glad you got it working...*

---

