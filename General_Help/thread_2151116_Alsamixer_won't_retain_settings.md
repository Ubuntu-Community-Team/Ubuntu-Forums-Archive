---
title: "Alsamixer won't retain settings"
date: 2013-06-03
forum: General Help
---

### Post by jimfl on 2013-06-03
I get no sound on bootup and have to run alsamixer to tell it to use my sound card instead of the default. Then I have to force alsa to reload. Because alsamixer doesn't retain the setting, I have to do this every time I bootup.

I've tried this with no success:
sudo alsactl store   (had to run it as root, though)

Any help appreciated.

---

### Post by CatKiller on 2013-06-03
I think trying to forcefully save your volume settings as a way to set your default sound device is probably doing it wrong.

ALSA has a configuration file for that kind of thing. asound.conf? Something like that. I haven't really played with ALSA much.

---

### Post by slickymaster on 2013-06-03
Take a look at this bug, [Sound muted after boot]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732"), in particular see posts [#3]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/3") and [#77]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/77")

---

### Post by LewisTM on 2013-06-03
Find you desired sound settings in alsamixer then store them
```
sudo alsactl store
```
Apply the settings, typically in a user autostart entry
```
alsactrl restore 
```

Cheers!

---

### Post by jimfl on 2013-06-05
LewisTM,

I used 
sudo alsactl store   and got Permission Denied error.

Tried gksudo alsactl store    and that seemed to work.

However, I don't know how to do a "user autostart entry."

---

