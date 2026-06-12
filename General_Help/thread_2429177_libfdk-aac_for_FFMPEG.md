---
title: "libfdk-aac for FFMPEG"
date: 2019-10-14
forum: General Help
---

### Post by zappor on 2019-10-14
[SIZE=2][FONT=arial]Good day

I have installed [COLOR=#24292E]libfdk-aac-dev to use FFMPEG

I am getting the following error: [/COLOR]error while loading shared libraries: libfdk-aac.so.0: cannot open shared object file: No such file or directory

When I check I do not have that file. I do have: /usr/lib/x86_64-linux-gnu/libfdk-aac.so
/usr/lib/x86_64-linux-gnu/libfdk-aac.so.1
/usr/lib/x86_64-linux-gnu/libfdk-aac.so.1.0.1

Why would there not be a: libfdk-aac.so.0?

What is the best way to solve this? Can I just download libfdk-aac.so.0 and from where?

I am using 16.04

Thank you[/FONT][/SIZE]

---

### Post by #&amp;thj^% on 2019-10-14
I'm assuming that you compiled FFMPEG from source?? [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)
This guide already includes everything you need to gain support for libfdk_aac in ffmpeg because --enable-libfdk_aac and --enable-nonfree are already present in the ./configure line for ffmpeg.

---

### Post by mc4man on 2019-10-14
Without addressing where or how you got ffmpeg, ect.., you could simply 
```
sudo apt-get install libfdk-aac0
```

---

### Post by zappor on 2019-10-15
Thanks 1fallen

It wasn't from source but downloading the file worked

Regards

---

### Post by zappor on 2019-10-15
It worked!

Thanks mc4man

Regards

---

