---
title: "Sound not working"
date: 2016-02-18
forum: General Help
---

### Post by geigermark on 2016-02-18
Hello guys,

i did a lot of research on this issue, and all mentioned solutions did not solve my problem.

If i go to System Settings > Multimedia i can see "dummy device", there are 2 other devices written in grey. i cant select them.

Some more information:

```

aplay -l
aplay: device_list:268: no soundcards found...

```

```

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)

```

```

cat /proc/asound/cards
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd3610000 irq 30

```

I tried several things like reinstalling alsa-utils, restarting alsa, editing some lines in /etc/modprobe.d/alsa-base.conf.
But nothing seemed to work.

Thanks for your help.
Kind regards.

---

### Post by ajgreeny on 2016-02-18
Have you looked in the terminal with command alsamixer?

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

You may find something is muted and therefore not giving sound output.

Pulseaudio-volume-control is also worth using as it gives another way of controlling audio output to hardware.

---

### Post by geigermark on 2016-02-18
When i try to run alsamixer i get following:

```

alsamixer
cannot open mixer: No such file or directory

```

Hmm but im sure that it has worked some time ago, back then i was making sure that nothing was muted.
I think thats not the problem.

---

### Post by ajgreeny on 2016-02-18
Install **alsa-utils** if you do not have it and that should give you alsamixer.

Is this a new install of Ubuntu?  I thought that package was part of the default installation of all the *ubuntu OSs, but perhaps I'm wrong; was it Ubuntu with unity desktop or another DE version that you installed?

---

### Post by geigermark on 2016-02-20
Okay, i was using Ubuntu 15.10 (with KDE, upgraded multiple times from 13.04). I guess the system was messed up in some serious way. Alsa-utils is installed. But i still cant open alsamixer (see error above). Probably i have broken something because i already tried a lot of stuff to fix the sound issue.

I just did a new install of the OS because i had even more problems than just the sound, so the problem is fixed for me now.

Thanks for your help :)

---

