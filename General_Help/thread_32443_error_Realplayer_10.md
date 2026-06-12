---
title: "error: Realplayer 10"
date: 2005-05-07
forum: General Help
---

### Post by Euphogirl353 on 2005-05-07
Hi, I'm a new linux user and just recently installed realplayer 10.0.4.750. When I try to open a file (.ram) it gives the error message:
"Cannot open the audio device. Another application may be using it."
Any help on how I can fix this?
Thanks!
Tara

PS I downloaded it into /opt/realplayer

---

### Post by NeoChaosX on 2005-05-07
Close all other applications using sound, then do "killall esd" in the console. Of course, if you don't want to do this everytime you want to run Real, you can hack  RealPlayer with [these](http://ubuntuforums.org/showpost.php?p=80282&postcount=21) instructions.

---

### Post by kvidell on 2005-05-07
[QUOTE=NeoChaosX]Close all other applications using sound, then do "killall esd" in the console. Of course, if you don't want to do this, you can hack the RealPlayer script with [these](http://ubuntuforums.org/showpost.php?p=80282&postcount=21) instructions.[/QUOTE]
 Aside from closing obvious applications, it's good to just check to make sure there's nothing else running in the background:
```
lsof | grep dsp
```That'll do ya.
Kill anything that shows up if you don't want it (esd for instance has a habbit of showing up).
- Kel

---

