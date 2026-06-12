---
title: "Gaim headache."
date: 2006-11-15
forum: General Help
---

### Post by pyrokinetic on 2006-11-15
Rawr, 

For some stupid reason none of the Gaim sounds work on my system, I have to keep watching for the window to flash which is frustrating as all hell for me, I went to the Gaim website and read the FAQ and followed these instructions..

> How do I get sound to work correctly?
    Gaim uses libao to play sounds. Playing sounds directly through esound or arts is no longer supported.

    Libao is a cross-platform library that allows programs to output PCM audio data to the native audio devices on a wide variety of platforms. It currently supports OSS (Open Sound System), ESD (ESounD), ALSA (Advanced Linux Sound Architecture), Sun audio system (used in Solaris, OpenBSD, and NetBSD), aRts (Analog Realtime Synthesizer).

    To compile Gaim with support for libao you need libao-devel and audiofile-devel. To use libao you need libao and audiofile. If you do not wish to install these packages you can also just change your sound playing method in preferences to Command and use esdplay %s or artsplay %s.
How do I make Gaim use ALSA or OSS for playing sounds? What does the "Automatic" option do?
    If you choose "Automatic", "ESD", or "Arts", Gaim uses libao to play sounds. Choosing "ESD" or "Arts" forces libao to play sounds using that method, while choosing "Automatic" lets it decide for itself.

    If you choose "Automatic", you can create a file, either /etc/libao.conf or ~/.libao, and put one of the following lines in it:

    default_driver=alsa
    default_driver=oss

    Other drivers, like alsa09, arts, esd, irix, macosx, nas, and sun might also be supported, depending on your platform and how libao was compiled. See also man 5 libao.conf.


and I still get nothing. :mad: anyone got any advice?

---

