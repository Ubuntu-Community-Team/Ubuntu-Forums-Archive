---
title: "can't compile VLC-0.8.0"
date: 2004-11-15
forum: General Help
---

### Post by tanari on 2004-11-15
can't do 'make' operation

```
: undefined reference to `pp_postprocess'
./modules/codec/ffmpeg/libffmpeg.a(libffmpeg_a-postprocess.o)(.text+0x 6f4): In function `ClosePostproc__ffmpeg':
: undefined reference to `pp_free_mode'
./modules/codec/ffmpeg/libffmpeg.a(libffmpeg_a-postprocess.o)(.text+0x 702): In function `ClosePostproc__ffmpeg':
: undefined reference to `pp_free_context'
collect2: ld returned 1 exit status
make[2]: *** [vlc] Error 1
make[2]: Leaving directory `/home/andrei/progi/vlc-0.8.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andrei/progi/vlc-0.8.0'
make: *** [all] Error 2
andrei@ubuntu:~/progi/vlc-0.8.0 $ 
```

---

### Post by chien on 2004-11-15
is it worth to try to install VLC 8.0?

so far 0.7.2 is doing the job, as easy as apt-get install vlc

---

### Post by jdong on 2004-11-15
0.8 is in Hoary.

---

