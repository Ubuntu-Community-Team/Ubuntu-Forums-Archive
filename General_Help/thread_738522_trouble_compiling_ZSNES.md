---
title: "trouble compiling ZSNES"
date: 2008-03-28
forum: General Help
---

### Post by GSZX1337 on 2008-03-28
I can't seem to get ZSNES to compile for me. I'm on an AMD 64 machine so I can't grab it off the repos. I know of that .deb for AMD 64 (ZSNES32) but the audio won't work for me. I'm trying to compile it from source and see if that will just work. It passes the configuration, but when I tell it to make, it gives me:

```

/usr/bin/ld: i386 architecture of input file `linux/sdlintrf.o' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
make: *** [main] Error 1

```
I just pasted that last few lines to keep from stretching the post, if the full code is needed, please say so.

Any help would be appreciated.

---

### Post by nsche on 2008-03-28
You need to recompile and rebuild that library for x64 also.  You somehow have a 32 bit version of whatever library that is.

---

### Post by GSZX1337 on 2008-03-28
> **nsche said:**
> You need to recompile and rebuild that library for x64 also. 

How can I do that?

> You somehow have a 32 bit version of whatever library that is.

ZSNES is 32-bit only. Am I screwed?

---

### Post by GSZX1337 on 2008-03-29
Bump.

---

### Post by Don Giovanni on 2008-03-30
I don;t know if you have seen this thread
[http://ubuntuforums.org/showthread.php?t=588744&highlight=http%3A%2F%2Fpackages.dfreer.org%3A8080](http://ubuntuforums.org/showthread.php?t=588744&highlight=http%3A%2F%2Fpackages.dfreer.org%3A8080)

dfreer setup his own repository to help with this (though it is down).  If you read through his first post he has instructions on compiling Zsnes for 64bit but states that the only way he has been able tto do it is use a 32bit OS to compile it first then transfer over the files.

Should be an easier way than that, but its all I have found :P

---

### Post by GSZX1337 on 2008-03-31
I managed to get the audio working in ZSNES32. Thanks for your help anyways.

---

