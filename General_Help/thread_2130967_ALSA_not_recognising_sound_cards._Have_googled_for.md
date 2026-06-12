---
title: "ALSA not recognising sound cards. Have googled for hours"
date: 2013-03-31
forum: General Help
---

### Post by 42f87d89 on 2013-03-31
I have spent a good deal of time trying to fix this problem and I feel I need direct help.

I am using Ubuntu server 12.04.2 and I installed alsa-base alsa-utils and alsa-tools

cat /proc/asound/cards produces this output:
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5500000 irq 46
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf5000000 irq 16

```

However aplay -l produces this output:
```

**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:4699:(snd_config_expand) Load defaults error: File exists
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:261: control open (0): File exists
ALSA lib conf.c:4699:(snd_config_expand) Load defaults error: File exists
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL hw:1
aplay: device_list:261: control open (1): File exists

```

and alsamixer:
```

ALSA lib control.c:841:(snd_ctl_open_conf) Invalid type for CTL default definition
cannot open mixer: Invalid argument

```

EDIT: I figured I had no default settings, so I went ahead and made the file ~/.asoundrc
```
pcm.!default {
    type plughw
    card 1
    device 0
}

ctl.!default {
    type plughw           
    card 1
    device 0
}
```
Where I changed "hw" to "plughw" and "card 0" to "card 1"

I got there from testing with:
aplay -D XXXXX /usr/share/sounds/alsa/Front_Center.wav

where XXXXX is plughw:0,0 or hw:0,0 and I kept changing the numbers "0,0" untill I got to "1,0"

---

### Post by 42f87d89 on 2013-04-07
Ok, so here is some more stuff.

I have a normal ubuntu 12.04.2 (non server) where alsa does work and has worked for a long time with no problems.
I deleted the partition I had with the ubuntu server I was having problems with and installed Arch. The problem is still there.

---

