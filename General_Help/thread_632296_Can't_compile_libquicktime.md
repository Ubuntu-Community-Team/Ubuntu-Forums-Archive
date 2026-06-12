---
title: "Can't compile libquicktime"
date: 2007-12-05
forum: General Help
---

### Post by honda on 2007-12-05
Hello, I'm trying to compile the libquicktime library. I got the source with
apt-get source libquicktime1

and got the dependences with 
sudo apt-get build-dep libquicktime1

./Configure ends with this error:
*config.status: error: cannot find input file: debian/Makefile.in*

Seems like it is looking for a Makefile.in  in ~/libquicktime-1.0.0+debian/debian? There is no such file there. 

What's wrong? I tried compiling the ffmpeg library the same way just to make sure the environment is set up correctly, and that worked without errors.

---

### Post by honda on 2007-12-05
bump

---

### Post by honda on 2007-12-06
The library crashes on my athlon xp, seems as it is compiled with SSE2, which athlon xp doesn't support. For instance open movie editor is unusable at the moment. Can someone please advice how to recompile the library?

---

### Post by honda on 2008-02-09
Well this is sort of funny.... I needed to recompile libquicktime again on a different machine, run into the same problem, and went to google for help. Quickly I found a promising link to the ubuntu forums, which turned out to be my own unanswered question... So I'll post the solution I found last time, at least I won't run into an unanswered post again when I have forgotten again... 

apt-get install apt-build

apt-build libquicktime1

---

