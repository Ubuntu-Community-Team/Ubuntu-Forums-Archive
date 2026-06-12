---
title: "sound problem in Feisty with a new laptop"
date: 2007-08-07
forum: General Help
---

### Post by patrick_g on 2007-08-07
Hello,

I have no sound at all with my new centrino laptop.
when i try a "sudo lspci -v" i have this :

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Rioworks Unknown device 2057
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```

When i go to System > Preferences > Sound and click some of the "Test" buttons, i cannot hear anything.
When i try a "aplay -l" i have this :

```
carte  0: Intel [HDA Intel], périphérique 0 : ALC260 Analog [ALC260 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC260 Digital [ALC260 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 6 : Si3054 Modem [Si3054 Modem]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
```

When i try "modinfo soundcore" i have this :

```
filename:       /lib/modules/2.6.20-16-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     45750F13477CBA5B6F36F46
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586
``` 

When i try "alsamixer" i have this :

[IMG]http://farm2.static.flickr.com/1122/1037417170_95db18fc77_b.jpg[/IMG]

I cannot understand why i have no sound at all. Any idea please ?

---

### Post by dragonwings on 2007-08-07
sudo asoundconf list
to get a list of soundcards you have ,take note of them

now
sudo asoundconf set-default-card (here is where you put your sound card name)


eg" for mine i put
sudo asoundconf set-default-card Audigy2

---

### Post by patrick_g on 2007-08-07
```
patrick@wide-laptop:~$ sudo asoundconf list
Password:
Names of available sound cards:
Intel
patrick@wide-laptop:~$ sudo asoundconf set-default-card Intel
```

After test there is still no sound :(

---

### Post by patrick_g on 2007-08-08
up

---

### Post by th_11 on 2007-08-08
I have also had sound problems in Feisty. And I'm not sure whats causing it exactly (no sound at all sometimes).

I did also check all those "modinfo soundcore" etc. stuff and it looked always good. But still the sound was sometimes gone..

Fortunately I found a (bit weird) solution that has fixed the problem for me.
I just go to System > Preferences > Sound and do nothing but click "Close" and immediately after that  reboot the machine and kaboom! The sound is back.

P.S. I have integrated sound chip and SoundBlasted card and if in that Sound windows Mixers default channel is VIA 8237 I always change it to SB Live! and then close the window.

P.P.S. Silly guestion, but are you sure that the laptop is not on mute?

---

### Post by patrick_g on 2007-08-08
Yes i'm sure my laptop is not on mute.
I think it's because my audio chip (ALC260) is not supported by ALSA.
Perhaps i will have better luck with Gutsy ? I will try the next Gutsy alpha version to see if there is improvement.

---

### Post by patrick_g on 2007-08-10
No problem at all with Gutsy Tribe 4 : the sound work.
Great !

---

