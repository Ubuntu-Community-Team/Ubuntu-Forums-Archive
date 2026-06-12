---
title: "Macromedia FlashPlayer Standalone (Projector)"
date: 2005-10-04
forum: General Help
---

### Post by buzzi22 on 2005-10-04
Hi there!
Has anyone tried to install StandalonePlayer 6 r79! I tried 2 ways but it won&#180;t work!
1.way: i downloaded it from macromedia site -untar - ./gflashplayer -- then he misses some library files!
2.way :apt-get install libflash-swfplayer , then tried ti open a file : swfplayer -root test.swf :
starting flashparser
flashparser done
free(): invalid pointer 0xb7c56008
open dsp: No such file directory!

Anyone an idea how to fix this problem ?!:rolleyes:

---

### Post by buzzi22 on 2005-10-05
noone an idea?

---

### Post by Xumbi on 2005-10-05
It looks like it can't find /dev/dsp, which isn't used in alsa (as far as I know).  I read somewhere that if you insert module snd-pcm-oss it will create /dev/dsp and be compatible with alsa.

So try this:

sudo modprobe snd-pcm-oss

Post your results.

---

### Post by buzzi22 on 2005-10-06
ok, i got it!
I downloaded FlashPlayer standalone 6 from macromedia site!
then: apt-get install libstdc++**6**
then i manually downloaded libstdc++-libc6.2-2.so.3 and put ir in /usr/lib. 
works fine :)

---

