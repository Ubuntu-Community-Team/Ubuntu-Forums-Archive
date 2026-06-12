---
title: "Can someone help me compile  this program?"
date: 2006-08-11
forum: General Help
---

### Post by UltraSonicSite on 2006-08-11
It seems that I never meet the requirments for compiling a program. There is always an error stopping me from achieving my simple goal of running the damn thing. #-o 

But I wont get aggrivated because it always seems like there is a decievingly simple solution to all my linux related problems. So I will assume that   position on "This Week's Compile Error!"

The culprit: "Ultimate Stunts"
The Problem: Compile error
The Terminal:
> Making all in ultimatestunts
make[2]: Entering directory `/home/ultrasonicsite/Desktop/ultimatestunts-srcdata-0611/ultimatestunts'
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I../intl -I../shared -I../simulation -I../graphics    -Wall -g -O2  -I/usr/include/SDL -D_REENTRANT -MT sndsample.o -MD -MP -MF ".deps/sndsample.Tpo" \
          -c -o sndsample.o `test -f 'sndsample.cpp' || echo './'`sndsample.cpp; \
        then mv -f ".deps/sndsample.Tpo" ".deps/sndsample.Po"; \
        else rm -f ".deps/sndsample.Tpo"; exit 1; \
        fi
sndsample.cpp: In member function ‘virtual bool CSndSample::load(const CString&, const CParamList&)’:
sndsample.cpp:111: error: invalid conversion from ‘ALubyte*’ to ‘const ALchar*’
sndsample.cpp:111: error:   initializing argument 1 of ‘void* alGetProcAddress(const ALchar*)’
sndsample.cpp:137: error: invalid conversion from ‘ALubyte*’ to ‘const ALchar*’
sndsample.cpp:137: error:   initializing argument 1 of ‘void* alGetProcAddress(const ALchar*)’
sndsample.cpp:162: error: ‘alutLoadWAV’ was not declared in this scope
make[2]: *** [sndsample.o] Error 1
make[2]: Leaving directory `/home/ultrasonicsite/Desktop/ultimatestunts-srcdata-0611/ultimatestunts'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ultrasonicsite/Desktop/ultimatestunts-srcdata-0611'
make: *** [all] Error 2
ultrasonicsite@ubuntu:~/Desktop/ultimatestunts-srcdata-0611$


I not being a developer have no idea whats wrong with sndsample.o
I have downloaded everything required to compile six times and downloaded development packages.

The page:[http://www.ultimatestunts.nl/documentation/en/compile.htm](http://www.ultimatestunts.nl/documentation/en/compile.htm)

The reason: Unknown

Can someone fill me in on this error, or try to help me start from the beginning step by step?

---

### Post by UltraSonicSite on 2006-08-11
I doubt it's such a hard problem.

---

### Post by Ziggurat on 2006-08-11
Is a codig error, try to get other version or fill a bug to the developers.

---

### Post by xXx 0wn3d xXx on 2006-08-11
I'll try and compile it and see what happens. If I suceed, I will package it and upload it.

---

### Post by UltraSonicSite on 2006-08-11
> **xXx 0wn3d xXx said:**
> I'll try and compile it and see what happens. If I suceed, I will package it and upload it.

Okay thanks alot.  :)

---

### Post by xXx 0wn3d xXx on 2006-08-11
> **UltraSonicSite said:**
> Okay thanks alot.  :)

I was able to compile it and statisfy most dependencies but I was not able to satisfy the sound dependency but I was able to continue without solving it. I am uploading now and I will post the link in about 6 minutes.

---

### Post by UltraSonicSite on 2006-08-11
> **xXx 0wn3d xXx said:**
> I was able to compile it and statisfy most dependencies but I was not able to satisfy the sound dependency but I was able to continue without solving it. I am uploading now and I will post the link in about 6 minutes.

Thank you very much. I know you've done quite a bit (I would assume) but could you tell me like what dependencies you downloaded as well as what errors you may have gotten and how you fixed them? You know, how did you do it? I'm willing to learn :D

---

### Post by UltraSonicSite on 2006-08-11
compiling an earlier version compiled further, but got some sort of alsa error.

---

### Post by xXx 0wn3d xXx on 2006-08-11
> **UltraSonicSite said:**
> compiling an earlier version compiled further, but got some sort of alsa error.

I installed libsdl-gfx1.2-dev and libsdl-image1.2 to fix the graphics problem. And I can't fix the sound problem but maybe you will get a different result I have tried:
> 
libasound2
libasound2-dev 
libsdl-sound1.2 
libsdl-sound1.2-dev 
libsndfile0 
libseal1 
libstk0-dev

Edit: Try installing libwavpack-dev and libwavpack0 and see if it fixes the problem.

---

### Post by UltraSonicSite on 2006-08-11
> **xXx 0wn3d xXx said:**
> I installed libsdl-gfx1.2-dev and libsdl-image1.2 to fix the graphics problem. And I can't fix the sound problem but maybe you will get a different result I have tried:


Edit: Try installing libwavpack-dev and libwavpack0 and see if it fixes the problem.

Ok I'm installing the packages and will tell you what happens in a few

---

### Post by UltraSonicSite on 2006-08-11
Didnt work:> Making all in ultimatestunts
make[2]: Entering directory `/home/ultrasonicsite/Desktop/ultimatestunts-srcdata-0601/ultimatestunts'
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I../intl -I../shared -I../simulation -I../graphics    -Wall -g -O2  -I/usr/include/SDL -D_REENTRANT -MT sndsample.o -MD -MP -MF ".deps/sndsample.Tpo" \
          -c -o sndsample.o `test -f 'sndsample.cpp' || echo './'`sndsample.cpp; \
        then mv -f ".deps/sndsample.Tpo" ".deps/sndsample.Po"; \
        else rm -f ".deps/sndsample.Tpo"; exit 1; \
        fi
sndsample.cpp: In member function ‘virtual bool CSndSample::load(const CString&, const CParamList&)’:
sndsample.cpp:111: error: invalid conversion from ‘ALubyte*’ to ‘const ALchar*’
sndsample.cpp:111: error:   initializing argument 1 of ‘void* alGetProcAddress(const ALchar*)’
sndsample.cpp:137: error: invalid conversion from ‘ALubyte*’ to ‘const ALchar*’
sndsample.cpp:137: error:   initializing argument 1 of ‘void* alGetProcAddress(const ALchar*)’
sndsample.cpp:162: error: ‘alutLoadWAV’ was not declared in this scope
make[2]: *** [sndsample.o] Error 1
make[2]: Leaving directory `/home/ultrasonicsite/Desktop/ultimatestunts-srcdata-0601/ultimatestunts'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ultrasonicsite/Desktop/ultimatestunts-srcdata-0601'
make: *** [all] Error 2
ultrasonicsite@ubuntu:~/Desktop/ultimatestunts-srcdata-0601$


---

### Post by UltraSonicSite on 2006-08-11
Did you get to upload the file?

---

### Post by xXx 0wn3d xXx on 2006-08-11
> **UltraSonicSite said:**
> Did you get to upload the file?

I'm trying to upload it but it keeps stalling and then timing out. Let me try some different sites.

---

### Post by UltraSonicSite on 2006-08-11
> **xXx 0wn3d xXx said:**
> I'm trying to upload it but it keeps stalling and then timing out. Let me try some different sites.

okay.

---

### Post by UltraSonicSite on 2006-08-12
Couldn't upload it?

---

### Post by UltraSonicSite on 2006-08-12
Guess not. =(

---

