---
title: "Realtek Audio Drivers problem."
date: 2016-08-07
forum: General Help
---

### Post by nourt1 on 2016-08-07
Hi! I'm not exactly a newbie to Ubuntu, since I used 15.04 before. I have nothing wrong in it so far, save for one problem: That I can't install Realtek Audio drivers.

I have followed their official guide on how to install drivers, but then I got this problem:

In function ‘snd_info_version_read’:
/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.c:1065:22: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
       "Compiled on " __DATE__ " for kernel %s"
                      ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.o' failed
make[3]: *** [/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.o] Error 1
scripts/Makefile.build:403: recipe for target '/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore' failed
make[2]: *** [/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore] Error 2
Makefile:1403: recipe for target '_module_/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa' failed
make[1]: *** [_module_/home/nour/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-31-generic'
Makefile:167: recipe for target 'compile' failed
make: *** [compile] Error 2


Now, to clear a confusion, my sound works because it uses the Intel HD Audio. But when I tried to record a video using Kazam, The desktop sound is not recording. (And yes, I checked 'Sound from Desktop' thing.)

So, any help? Thank you very much.

Laptop Specs *if needed*:
Lenovo Z51-70
Intel Core i7
Realtek HD Audio.
Windows 8.1 dual booted with Ubuntu 16.04 LTS.

---

### Post by Geoffrey_Arndt on 2016-08-07
If your audio system is working - except for a certain program or two, I would caution against re-building (compiling) new audio driver.    Often, that's a good way to ruin all audio on the whole system, and may require repeated compiling whenever the kernel gets updated (which happens a LOT).

Have you watched or tried this yet . . . . [https://www.youtube.com/watch?v=g4e52FRo3Vc](https://www.youtube.com/watch?v=g4e52FRo3Vc)

---

### Post by nourt1 on 2016-08-09
How do I go to PulseAudio Volume Control?

---

### Post by nourt1 on 2016-08-09
How do I go to PulseAudio Volume Control?

---

