---
title: "No audio"
date: 2013-12-13
forum: General Help
---

### Post by Notasoddingclue on 2013-12-13
After spending a month offline with the computer I had over 40 updates to install.  All of which was successful apart from a few that came the next day.

But after the update on the 12.10 all audio does not work.  When turning on it is fin and when in guest, that also is fine.  But there is no audio at all in the main user.

I looked at sound and the settings have changed.  I can not move the sliders to get any audio.  It seems that it is not part of any program.  Furthermore, ALSA mixer refuses to show and when powering down the system says it is still in use.

So any help on getting it back to decent audio?

---

### Post by Yellow Pasque on 2013-12-13
First, delete the problematic user's pulse config files (pulseaudio will regenerate them on next restart) :
```
sudo rm -r ~/.pulse*
pulseaudio -k
```

If that doesn't work, gice more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Notasoddingclue on 2013-12-13
That worked.  But now my home files are on my desktop and my desktop is now home.

May as well redo my system and dig out the OS disc.

---

