---
title: "[SOLVED] Change modprobe sequence"
date: 2008-03-21
forum: General Help
---

### Post by ChrisMP1 on 2008-03-21
BG info:
I have a HP/Compaq Presario C751 (Conexant 5051/Intel HDA). The sound was not working correctly -- i.e., the main speakers would not shut off when headphones were plugged in. I corrected the problem by compiling and upgrading ALSA to 1.0.16.

The problem is that now modprobe won't work to start up the sound card (it won't start on boot!). I have to use insmod, and in a very specific order. I use the following simple shell script to start it up:
```
#!/bin/bash

/etc/init.d/alsasound stop

cd /lib/modules/2.6.22-14-generic/updates/sound
insmod soundcore.ko
insmod snd.ko
insmod snd-mixer-oss.ko
insmod snd-seq-device.ko
insmod snd-timer.ko
insmod snd-hwdep.ko
insmod snd-pcm.ko
insmod snd-pcm-oss.ko
insmod snd-rtctimer.ko
insmod snd-seq.ko
insmod snd-seq-midi-event.ko
insmod snd-seq-oss.ko

```

I really don't care about getting modprobe to work, but how can I make this happen automatically? (Gracefully! Of course I can work it into /etc/init.d and /etc/rc2.d, but that's just dumb.)

---

### Post by bingoUV on 2008-03-22
you could try putting it into /etc/rc.local. I believe it would be considered graceful.

---

### Post by dcstar on 2008-03-22
> **ChrisMP1 said:**
> BG info:
I have a HP/Compaq Presario C751 (Conexant 5051/Intel HDA). The sound was not working correctly -- i.e., the main speakers would not shut off when headphones were plugged in. I corrected the problem by compiling and upgrading ALSA to 1.0.16.

The problem is that now modprobe won't work to start up the sound card (it won't start on boot!). I have to use insmod, and in a very specific order. I use the following simple shell script to start it up:
```
#!/bin/bash

/etc/init.d/alsasound stop

cd /lib/modules/2.6.22-14-generic/updates/sound
insmod soundcore.ko
insmod snd.ko
insmod snd-mixer-oss.ko
insmod snd-seq-device.ko
insmod snd-timer.ko
insmod snd-hwdep.ko
insmod snd-pcm.ko
insmod snd-pcm-oss.ko
insmod snd-rtctimer.ko
insmod snd-seq.ko
insmod snd-seq-midi-event.ko
insmod snd-seq-oss.ko

```

I really don't care about getting modprobe to work, but how can I make this happen automatically? (Gracefully! Of course I can work it into /etc/init.d and /etc/rc2.d, but that's just dumb.)

**/etc/modules** contains what you can force to load at boot time, and you may have to put those in the **/etc/modprobe.d/blacklist** file if they still get loaded by the system (I'm not sure about this, though).

---

### Post by ChrisMP1 on 2008-03-22
> you could try putting it into /etc/rc.local. I believe it would be considered graceful.

:) Graceful enough. I forgot all about rc.local...

---

