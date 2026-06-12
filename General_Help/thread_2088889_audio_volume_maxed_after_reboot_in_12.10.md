---
title: "audio volume maxed after reboot in 12.10"
date: 2012-11-27
forum: General Help
---

### Post by TylerBraun on 2012-11-27
I recently upgraded to 12.10 and since I did my volume is maxed every time I start up my computer. I've checked the sound settings and don't see anything new about default startup volume or anything. Is there a new setting somewhere I haven't found yet or is this a bug? As much as I don't think it could be a hardware issue as I've been using this computer since 7.04, the fact that I can't find any information on it suggests it may be. I am running a Dell Inspiron 1525 with (Dell says) a STAC 92XX C-Major HD Audio.

---

### Post by kostkon on 2012-11-27
Try resetting your pulseaudio configuration. Open, your home folder, press CTRL+H to show hidden files and then find and delete the folder named .pulse. Alternativey, in the terminal give:
```
rm -rf ~/.pulse
```

then logout and login again.

Afterwards, if needed, just open your sound preferences to configure your sound again.

---

### Post by TylerBraun on 2012-11-27
> **kostkon said:**
> Try resetting your pulseaudio configuration. Open, your home folder, press CTRL+H to show hidden files and then find and delete the folder named .pulse. Alternativey, in the terminal give:
```
rm -rf ~/.pulse
```

then logout and login again.

Afterwards, if needed, just open your sound preferences to configure your sound again.

So I renamed .pulse to .pulse.bak instead and logged out and in. I tried adjusting my volume and nothing happened so I went into the sound settings and there was no hardware present so I deleted the new .pulse and restored my backup, logged out and in, and now it is working properly, even remembering the volume after logging out and in. So it's solved, but I'm not sure how it happened.

---

### Post by kostkon on 2012-11-27
> **TylerBraun said:**
> So I renamed .pulse to .pulse.bak instead and logged out and in. I tried adjusting my volume and nothing happened so I went into the sound settings and there was no hardware present so I deleted the new .pulse and restored my backup, logged out and in, and now it is working properly, even remembering the volume after logging out and in. So it's solved, but I'm not sure how it happened.
Hmmm, interesting. Maybe a hardware volume level or switch got reset after the new pulse config was loaded or maybe it was a permissions problem with your old folder and now that you put it back it acquired the corrent ones. or something else I can't think of :P

---

