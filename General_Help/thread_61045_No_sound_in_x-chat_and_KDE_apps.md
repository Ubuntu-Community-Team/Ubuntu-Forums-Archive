---
title: "No sound in x-chat and KDE apps"
date: 2005-08-30
forum: General Help
---

### Post by Zalbor on 2005-08-30
Sound works perfectly in all GNOME applications and other programs that (as far as I know) don't use GTK, like the games Enigma and Tuxracer or emulators such as dosbox. But x-chat can't produce any sound, when I try to set up .wav files to be played in certain occasions (such as when someone says my name).
Also the sound doesn't work in KDE applications, which isn't as important to me as in x-chat. Someone told me I need to re-compile alsa, is that the only way?

---

### Post by Lord Illidan on 2005-08-30
Try typing

```
killall esd
```

before launching the app..

---

### Post by Zalbor on 2005-08-30
Yes, that worked! Thank you :)

---

### Post by Zalbor on 2005-08-30
[QUOTE=Zalbor]Yes, that worked! Thank you :)[/QUOTE]
 Um, side effect... It removed the sound from gnome itself and other programs...

---

### Post by Zalbor on 2005-09-24
Sorry to bump this, but I'd really like to find a way to solve it...

---

