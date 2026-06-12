---
title: "Sound Driver Error"
date: 2005-09-07
forum: General Help
---

### Post by karuptdata on 2005-09-07
I am tryin to compile module for my sound driver however when i enter this command 

./configure --with-cards=es18xx --with-sequencer=yes;make;make install it gets through some of it and then i get this error message:
```

make -C /lib/modules/2.6.12-8-386/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.9b  modules
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-386'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.o] Error 127
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.9b/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.9b] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-386'
make: *** [compile] Error 2
find /lib/modules/2.6.12-8-386/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
mkdir -p /lib/modules/2.6.12-8-386/kernel/sound/acore
cp snd-hpet.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.12-8-386/kernel/sound/acore
cp: cannot stat `snd-hpet.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
make: *** [install-modules] Error 1
```

Does anyone know how to fix it??

---

### Post by skoal on 2005-09-07
karuptdata, I don't understand.  You've posted another thread just like this one, and now you post another here.  Also, me and azz asked you if you had checked that ESS wiki link in your original thread (3rd link), but you never replied back in that thread.

What's up?  We can't help you unless you step through the troubleshooting process with us.  Making 3 redundant posts only makes it more difficult to help...

\\//_

---

### Post by bastijn on 2005-09-25
Alloa,

I have a really strange problem with my sound. The first time i putted in the live-CD i had sound. Then I installed it on my laptop and i had sound. After this the apt-get update and from then of i have no sound. My sound-pictogram in the upper right corner shows an X and when i click it, it sais something like: "Maybe your card aint installed or GStreamer-plugin is not right." Acording to my laptop I have an 'intel 82801BA-ICH2' sound card. Can anyone help me?

PS. I use ubuntu 5.10, installed it on sunday sept 25 and updated it sept 25.

Greetz,
Bastijn

---

### Post by fordfan753 on 2005-09-25
> **karuptdata]I am tryin to compile module for my sound driver however when i enter this command 

./configure --with-cards=es18xx --with-sequencer=yes said:**
> : gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-386'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.o] Error 127
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.9b/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.9b] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-386'
make: *** [compile] Error 2
find /lib/modules/2.6.12-8-386/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
mkdir -p /lib/modules/2.6.12-8-386/kernel/sound/acore
cp snd-hpet.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.12-8-386/kernel/sound/acore
cp: cannot stat `snd-hpet.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
make: *** [install-modules] Error 1
```

Does anyone know how to fix it??


Install the build-essential package and make sure you have gcc-3.4-dev insttalled.
Hmm, would this be a problem with Breezy using gcc-4.0? Come on, someone more qualified. :P

---

