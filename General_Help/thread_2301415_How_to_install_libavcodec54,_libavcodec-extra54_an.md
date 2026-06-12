---
title: "How to install libavcodec54, libavcodec-extra54 and libicu52 in ubuntu 15.10"
date: 2015-11-02
forum: General Help
---

### Post by fkervin on 2015-11-02
Hi All,

I've recently made a fresh install of my computer and has moved from 14.04 to newest 15.10.

I've found a problem with two programs that I was using with no problem but now I'm not able to install them. One of those programs requires libavcodec54 and libavcodec-extra54 but those seems to be no longer available for the 15.10 ubuntu version. The same for other program that asks for libicu52.

How can I make those programs install on 15.10?

Many thanks to anyone who read this

Regards

---

### Post by Linuxisfast on 2015-11-02
Have you tried installing ubuntu-restricted-extras and ffmpeg?

---

### Post by fkervin on 2015-11-02
> **Linuxisfast said:**
> Have you tried installing ubuntu-restricted-extras and ffmpeg?

Many thanks for your answer, Linuxisfast,

Yes, I installed xubuntu-restricted-extras and also xubuntu-restricted-addons (I use exactly xubuntu), I also installed ffmpeg as described here: 

[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

But as I told, I'm not able to install libavcodec54, libavcodec-extra54 nor libicu52

If I try to install from terminal using sudo apt-get, the system says that libavcodec54, libavcodec-extra54 can't be located. If I enter in Synaptic I see that the packages "libavcodec-dev" "libavcodec-ffmpeg56" "libavutil-ffmpeg54" and "libavutil-dev" are installed amont others, I'm not sure if those ones are related or replaces libavcodec54, libavcodec-extra54. The issue is actually that the program I want to install requires those two ones, but I'm not able to install them.

In case of libicu52 I get the message saying it has no candidate for installation. If I enter in synaptic I find that libicu55 is installed, so the problem clearly seems to be that libicu52 has been replacer for the newer version (libicu55), but the program I want to install needs older libicu52.

Any idea?

Many thanks

---

