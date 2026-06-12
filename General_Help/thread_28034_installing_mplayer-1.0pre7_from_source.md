---
title: "installing mplayer-1.0pre7 from source"
date: 2005-04-18
forum: General Help
---

### Post by gheorghe_pop on 2005-04-18
Hi!
This is the error that i get when i'm trying to 'make':
```
gcc-3.4 -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=athlon-xp -mtune=athlon-xp -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/freetype2    -I/usr/X11R6/include       -o mencoder.o mencoder.c
In file included from libmpdemux/dvbin.h:11,
                 from cfg-common.h:396,
                 from cfg-mencoder.h:6,
                 from mencoder.c:293:
libmpdemux/dvb_defaults.h:73:3: warning: #warning No DVB-T country defined in dvb_defaults.h, defaulting to UK. Ignore this if using Satellite or Cable.
mencoder.c: In function `lame_presets_set':
mencoder.c:2038: error: `MEDIUM_FAST' undeclared (first use in this function)
mencoder.c:2038: error: (Each undeclared identifier is reported only once
mencoder.c:2038: error: for each function it appears in.)
mencoder.c:2040: error: `MEDIUM' undeclared (first use in this function)
mencoder.c:2049: error: `STANDARD_FAST' undeclared (first use in this function)
mencoder.c:2051: error: `STANDARD' undeclared (first use in this function)
mencoder.c:2059: error: `EXTREME_FAST' undeclared (first use in this function)
mencoder.c:2061: error: `EXTREME' undeclared (first use in this function)
mencoder.c:2069: error: `INSANE' undeclared (first use in this function)
make: *** [mencoder.o] Error 1

``` 
Please HELP!!!!

---

### Post by NeoChaosX on 2005-04-18
Did you do ./configure first?

---

### Post by gheorghe_pop on 2005-04-18
yes!
./configure didn't give a error
I don't know what's wrong. Till now installing mplayer from source worked like a charm

---

### Post by Turin Turambar on 2005-04-18
Hmmm, yesterday I downloaded Mplayer pre7 version, I compiled it successfully but didn't have the sound (although ./configure said OSS presented). :(
Then I switched to VLC... now VLC is causing me trouble, but that's another story.

---

