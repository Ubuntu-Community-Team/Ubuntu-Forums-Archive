---
title: "Audio Stuttering 14.04"
date: 2016-05-06
forum: General Help
---

### Post by doug23 on 2016-05-06
This question has been asked and answered many times before and I have tried virtually everything suggested to date so I am out of things to try.

The problem is occasional and random stuttering of audio. The stuttering is just that, a quick repetition of a portion of a few words lasting maybe 2-3 seconds. of The system is a Lenovo 50-50 Ubuntu 14.04 64 bit Mate desktop. The standard alsa pulseaudio is installed. I use this system extensively and everything else works fine. My one complaint is the audio. If I am listening to audio this happens maybe once every 5-10 minutes but it is random and it does not seem to be related to anything else going on in the computer. I can be viewing TV with Kaffeine and surfing the web and it does not happen. Then just watching and doing nothing else it does. It also seems to only happen on playback. If I time shift with Kaffeine and it stutters and I go back over the same spot it does not again happen so the recording is not effected.

I have extensively read through the google hits on this subject and tried everything suggested. Nothing seemed to make much difference. The last thing I did which did seem to make some improvement was update alsa with dkms. It does seem to be happening less often but that is hard to determine since it is so random. I also have a better quality sound card installed and it does the same thing as the internal card. 

While this is annoying it is something I can probably live with as it does not seem to effect recordings. It would be nice to find some magical fix. Since the alsa update did seem to make things better my guess it is something there. 

A question I would have is are users that have never seemed to solve this problem in 14.04 seeing it fixed in 16.04? That would be something to try but I am not in a hurry to update.

---

### Post by T.J. on 2016-05-06
> **doug23 said:**
> This question has been asked and answered many times before and I have tried virtually everything suggested to date so I am out of things to try.

The problem is occasional and random stuttering of audio. The stuttering is just that, a quick repetition of a portion of a few words lasting maybe 2-3 seconds. of The system is a Lenovo 50-50 Ubuntu 14.04 64 bit Mate desktop. 

A question I would have is are users that have never seemed to solve this problem in 14.04 seeing it fixed in 16.04? That would be something to try but I am not in a hurry to update.



Please let me know if you need detailed instructions.  Sometimes, my short answers can be a little obscure. 

First and most important, The version of Kaffiene that many distributions ship is older and is essentially unmaintained ([https://www.mail-archive.com/kde-devel@kde.org/msg04046.html](https://www.mail-archive.com/kde-devel@kde.org/msg04046.html)). It has been in a state of limbo for years, although there have been some updates in the project's Git repository. It still uses the old libxine library, instead of KDE Phonon. Have you tested an alternative player?

One thing that you can do is to temporarily disable PulseAudio and test if the problem remains, .i.e in a terminal: *pulseaudio --kill *then test your sound with ALSA. Afterward, log out and then back in so PA is reloaded. Assuming you have an Intel HD audio chipset, and it does turn out to be PA, have you tried adjusting the timing for PulseAudio?


In the file /etc/pulse/default.pa (back it up first): 

Change this: 
```
### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect 
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect 
.endif

```

to this:

```
### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect tsched=0
.endif

```

You should reboot after making the edit, just to be sure.

It may help.  PulseAudio can have timing issues with a number of ALSA drivers.

---

### Post by doug23 on 2016-05-06
T.J.

Yes, as I stated I tried everything I could find including what you mentioned. I doubt I missed anything. What would be nice is something that would load it heavily, test it, and report the problem. Probably wishful thinking.

---

### Post by T.J. on 2016-05-08
It still stutters even with something like Parole?  That's impressive.  It might be one of the codecs on the system.  Do all files stutter or just certain types?

Another thought might be running top in a terminal at the same time and see if you are getting a processor spike when it stutters.  It may give some insight.  

If you have Neopmuk or Stringi semantics enabled under KDE I would temporarily disable them as well.

---

