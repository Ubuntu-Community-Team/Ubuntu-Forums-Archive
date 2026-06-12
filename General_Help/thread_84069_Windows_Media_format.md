---
title: "Windows Media format"
date: 2005-10-30
forum: General Help
---

### Post by joris.brus on 2005-10-30
I can't seem to play any wmv files. I hear sound but no video.
Xine, Totem and mplayer all don't work.
I untarred all files from the mplayer essential codec package into /usr/lib/win32
xine config file points to this location.
Can play divx, xvid and dvds fine

I have the amd64 version.

I also have an asus a8v motherboard and can't seem to get any audio out of my surround sound ports.

---

### Post by realwhz on 2005-10-30
Have you tried the multimedia howto in documantation of Ubuntu 5.10 exactly?  It should work in most scenarios.  After installing totme-xine, w32codecs and related packages, this problem may be solved.  Additionally, for mplayer, have you tried to specify the vo?  Try x11, xv etc.  Hope it is helpful.

---

### Post by AlexMR on 2005-10-30
Hello joris.brus,

as far as I know, the w32codecs are 32-bit only, so they probabely won&#180;t work with the 64-bit version you have installed.

Greets,
Alex.

---

### Post by joris.brus on 2005-10-30
I tried the -vo commands.. It comes up with an error that it can't find the wmv 

Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family

There seems to be a lot of problems with the 64 bit version, ie no flash, no realplayer and now this. Maybe I'll install the 32 bit version some time.

---

### Post by jrib on 2005-10-30
have you looked over [http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399) ?

---

### Post by joris.brus on 2005-10-30
Yeah I read that forum.. it's quite frustrating since it seems to work for everybody else. I have xine-totem and xine-ui, i followed those instructions and it simply doesn't work. 
I also just followed an how-to on building a chroot.. of course that fails as well. when doing the apt-get install I get errors complaining about locale not set and going back to default locale. I selected en_us

I hate life

---

