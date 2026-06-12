---
title: "no audio on headphones after update"
date: 2021-01-30
forum: General Help
---

### Post by dutchen18 on 2021-01-30
I have a Microsoft LifeChat LX-3000 headset and, after updating, I can still select it as the default audio device but all audio plays through a different device instead.
Surprisingly enough, Discord seems to be the only application that's still able to play audio through my headset.

I tried all the obvious things like replugging, rebooting, removing all other usb devices, but no luck.
I'm not sure what other information would be relevant here, just lmk and I'll provide more logs.

```
chen@chen-pc:~$ uname -a
Linux chen-pc 5.8.0-41-generic #46~20.04.1-Ubuntu SMP Mon Jan 18 17:52:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
chen@chen-pc:~$ pactl --version
pactl 13.99.1
Compiled with libpulse 13.99.0
Linked with libpulse 13.99.0
```

---

### Post by ActionParsnip on 2021-01-30
Please follow this and give the output of step 3 when you get there
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by dutchen18 on 2021-01-30
Step 3 from that page is "Can another user play one of these "known-good" sounds?"
Not sure what logs you want from that.
Running "aplay /usr/share/sounds/alsa/Front_Center.wav" from step 2 also plays through the correct device (my headphones)
After trying some more applications I'm actually having trouble finding ones that don't work, just seems to be firefox and sound settings that refuse to play through my headphones.

---

