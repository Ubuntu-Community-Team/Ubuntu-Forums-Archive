---
title: "Ubuntu 18.04 Compile error when trying to install Realtek High Definition Audio"
date: 2018-05-17
forum: General Help
---

### Post by rather-not on 2018-05-17
I'm trying to install high definition audio drivers following this guide: [https://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/](https://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/)

More than happy to provide more information if needed, not sure what the procedure for troubleshooting this problem would be, I've tried contacting Realtek support but haven't had a response in >2 months.

Motherboard: Gigabyte z68ap-d3

After the "make" command it errors out, this is the terminal output from when the first error shows:

```
/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:1002:2: error: unknown type name &#8216;wait_queue_t&#8217;; did you mean &#8216;wait_event&#8217;?  wait_queue_t wait;
  ^~~~~~~~~~~~
  wait_event
/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:1008:23: error: passing argument 1 of &#8216;init_waitqueue_entry&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
  init_waitqueue_entry(&wait, current);
                       ^
In file included from ./include/linux/mmzone.h:10:0,
                 from ./include/linux/gfp.h:6,
                 from ./include/linux/umh.h:4,
                 from ./include/linux/kmod.h:22,
                 from ./include/linux/module.h:13,
                 from /home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/include/adriver.h:50,
                 from /home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:2:
./include/linux/wait.h:79:20: note: expected &#8216;struct wait_queue_entry *&#8217; but argument is of type &#8216;int *&#8217;
 static inline void init_waitqueue_entry(struct wait_queue_entry *wq_entry, struct task_struct *p)
                    ^~~~~~~~~~~~~~~~~~~~
/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:1009:37: error: passing argument 2 of &#8216;add_wait_queue&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
  add_wait_queue(&card->power_sleep, &wait);
                                     ^
In file included from ./include/linux/mmzone.h:10:0,
                 from ./include/linux/gfp.h:6,
                 from ./include/linux/umh.h:4,
                 from ./include/linux/kmod.h:22,
                 from ./include/linux/module.h:13,
                 from /home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/include/adriver.h:50,
                 from /home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:2:
./include/linux/wait.h:150:13: note: expected &#8216;struct wait_queue_entry *&#8217; but argument is of type &#8216;int *&#8217;
 extern void add_wait_queue(struct wait_queue_head *wq_head, struct wait_queue_entry *wq_entry);
             ^~~~~~~~~~~~~~
/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:1022:40: error: passing argument 2 of &#8216;remove_wait_queue&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
  remove_wait_queue(&card->power_sleep, &wait);
                                        ^
In file included from ./include/linux/mmzone.h:10:0,
                 from ./include/linux/gfp.h:6,
                 from ./include/linux/umh.h:4,
                 from ./include/linux/kmod.h:22,
                 from ./include/linux/module.h:13,
                 from /home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/include/adriver.h:50,
                 from /home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.c:2:
./include/linux/wait.h:152:13: note: expected &#8216;struct wait_queue_entry *&#8217; but argument is of type &#8216;int *&#8217;
 extern void remove_wait_queue(struct wait_queue_head *wq_head, struct wait_queue_entry *wq_entry);
             ^~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.o' failed
make[3]: *** [/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/init.o] Error 1
scripts/Makefile.build:606: recipe for target '/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore' failed
make[2]: *** [/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore] Error 2
Makefile:1552: recipe for target '_module_/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa' failed
make[1]: *** [_module_/home/xxx/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
Makefile:167: recipe for target 'compile' failed
make: *** [compile] Error 2



```

---

### Post by dino99 on 2018-05-17
Check that: dkms, build-essential and the kernel-headers are installed before compiling the driver

---

### Post by rather-not on 2018-05-17
Upon trying to update these components it seems they're all up to date. 

dkms is already the newest version (2.3-3ubuntu9).

build-essential is already the newest version (12.4ubuntu1).

linux-headers-4.15.0-20-generic is already the newest version (4.15.0-20.21).

---

### Post by Yellow Pasque on 2018-05-17
The custom Realtek driver is too old to work with modern kernels. It is a dead end. Your audio should be working without any driver gymnastics. You should give more info on what the issue is that caused you to seek out a different driver.

---

### Post by rather-not on 2018-05-17
Sure, so on windows upon installing the realtek drivers my audio is louder without loss of quality.

 I've tried using the "over amplify" feature but it causes loss of quality. 

So my audio is quieter on Ubuntu, the same level as if I was using windows without the realtek drivers.

Hope that makes sense

---

### Post by Yellow Pasque on 2018-05-17
It makes sense. I assume you're using the default volume control in Ubuntu. Have you tried altering the levels in alsamixer?
```
alsamixer
```

You can get good detailed audio info with:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by rather-not on 2018-05-17
Yeah, everything's turned up on [COLOR=#000000][FONT=&quot]alsamixer[/FONT][/COLOR].

I've made sure I'm using the correct sound card and output device too.

Thanks for the help, by the way!

---

### Post by dino99 on 2018-05-17
Looks like kernel devs are baking some patches around 'unknown type name &#8216;wait_queue_t&#8217;' error
Maybe you will find more related discussion on the realtek forum/support

---

### Post by rather-not on 2018-05-17
Yeah, I thought due to my old hardware and the age of the realtek driver that it could be something I can't do much about.

I've attempted to email realtek support but have not gotten a response and It's been over two months now. I'll keep an eye out for the wait_queue_t error patch.

Thanks ever so much for your help though!

---

### Post by ImmortalSoFar on 2018-05-18
Having a similar (but worse) issue myself. Running Ubuntu Mate on an ASRock AB350. Sound shows up as HD Audio generic but it's stuck on mute, and doesn't play back at all.

---

### Post by Yellow Pasque on 2018-05-18
> **ImmortalSoFar said:**
> Having a similar (but worse) issue myself. Running Ubuntu Mate on an ASRock AB350. Sound shows up as HD Audio generic but it's stuck on mute, and doesn't play back at all.

Please start a new thread and give your alsa info:  [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

