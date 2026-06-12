---
title: "g++ not including alsa/asoundlib.h"
date: 2005-05-16
forum: General Help
---

### Post by linuxNewb on 2005-05-16
I'm running hoary on a Presario 900, everything, including sound, works great. 

I am very new to c/c++ so this might be very simple (crossing my fingers, lol). I apt-getted build-essential and libasound2-dev. I am trying to compile a simple recording program that I got from the documentation at [http://www.linuxjournal.com/node/6735/print](http://www.linuxjournal.com/node/6735/print) (Listing4). 

The necessary ALSA header files are in usr/include/alsa, but I think they are not being included properly, because I keep getting the following errors when trying to compile it:

$ g++ -o capture capture.cpp

/tmp/ccb6n0Qx.o(.text+0x2f): In function `main':
: undefined reference to `snd_pcm_open'
/tmp/ccb6n0Qx.o(.text+0x43): In function `main':
: undefined reference to `snd_strerror'
/tmp/ccb6n0Qx.o(.text+0x6d): In function `main':
: undefined reference to `snd_pcm_hw_params_sizeof'
/tmp/ccb6n0Qx.o(.text+0x84): In function `main':
: undefined reference to `snd_pcm_hw_params_sizeof'
/tmp/ccb6n0Qx.o(.text+0xad): In function `main':
: undefined reference to `snd_pcm_hw_params_any'
/tmp/ccb6n0Qx.o(.text+0xc7): In function `main':
: undefined reference to `snd_pcm_hw_params_set_access'
/tmp/ccb6n0Qx.o(.text+0xe1): In function `main':
: undefined reference to `snd_pcm_hw_params_set_format'
/tmp/ccb6n0Qx.o(.text+0xfb): In function `main':
: undefined reference to `snd_pcm_hw_params_set_channels'
/tmp/ccb6n0Qx.o(.text+0x122): In function `main':
: undefined reference to `snd_pcm_hw_params_set_rate_near'
/tmp/ccb6n0Qx.o(.text+0x149): In function `main':
: undefined reference to `snd_pcm_hw_params_set_period_size_near'
/tmp/ccb6n0Qx.o(.text+0x15b): In function `main':
: undefined reference to `snd_pcm_hw_params'
/tmp/ccb6n0Qx.o(.text+0x16f): In function `main':
: undefined reference to `snd_strerror'
/tmp/ccb6n0Qx.o(.text+0x1ad): In function `main':
: undefined reference to `snd_pcm_hw_params_get_period_size'
/tmp/ccb6n0Qx.o(.text+0x1dd): In function `main':
: undefined reference to `snd_pcm_hw_params_get_period_time'
/tmp/ccb6n0Qx.o(.text+0x226): In function `main':
: undefined reference to `snd_pcm_readi'
/tmp/ccb6n0Qx.o(.text+0x24f): In function `main':
: undefined reference to `snd_pcm_prepare'
/tmp/ccb6n0Qx.o(.text+0x262): In function `main':
: undefined reference to `snd_strerror'
/tmp/ccb6n0Qx.o(.text+0x2f6): In function `main':
: undefined reference to `snd_pcm_drain'
/tmp/ccb6n0Qx.o(.text+0x301): In function `main':
: undefined reference to `snd_pcm_close'
collect2: ld returned 1 exit status

Can anyone tell me what might be wrong? Thanks.

---

### Post by linuxNewb on 2005-05-16
found the solution, in case anyone else needs it, add '-lasound':

$ g++ -o capture capture.cpp -lasound

---

### Post by yabadabadoo on 2006-11-15
Hi friend,

thanx a lot... i wasted my 2 days  ](*,)  on solving this problem because of less help available on Net.

Thanx again.

---

