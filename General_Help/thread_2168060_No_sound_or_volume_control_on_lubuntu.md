---
title: "No sound or volume control on lubuntu"
date: 2013-08-16
forum: General Help
---

### Post by yesveryfunny666 on 2013-08-16
Recently done a fresh install of lubuntu. Mostly all good except there's no sound. The "volume control" panel doesn't show up on the taskbar. Finally (like my previous installation when the sound and volume control worked) my laptop shortcuts for volume don't work. Any help would be appreciated

---

### Post by newb85 on 2013-08-16
In know in regular (Unity) ubuntu, that volume control in the panel is the package "indicator-sound".  That may or may not be the case in LXDE.

---

### Post by yesveryfunny666 on 2013-08-16
No can't see that, just a "volume control" panel. It shows on the "currently loaded plugins" but is invisible on the taskbar. Is there any other way to view volume settings?

---

### Post by newb85 on 2013-08-16
Try this to see if indicator sounds is running
```
 ps -a | grep indicator-sound 
```

If it returns a process, run
```
 sudo kill *##*
```

Where ## is the number at the beginning of the line that first command returned.  It should restart automatically.

---

### Post by yesveryfunny666 on 2013-08-16
Nope nothing for that :(

---

### Post by newb85 on 2013-08-16
Hmm... perhaps try that with pavucontrol instead of indicator-sound?

---

### Post by yesveryfunny666 on 2013-08-18
Yep, installed pavucontrol and pulseaudio and now it's working, same as this [http://ubuntuforums.org/showthread.php?t=1969564](http://ubuntuforums.org/showthread.php?t=1969564)

Volume control still doesn't show up on the task bar

---

### Post by newb85 on 2013-08-19
Isn't volume control an applet that can simply be added to the Lubuntu panel?  (Right click the panel, click Add to panel...)

---

