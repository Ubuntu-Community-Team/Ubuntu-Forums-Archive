---
title: "libGL.so goes missing on reboot"
date: 2007-07-16
forum: General Help
---

### Post by allan175 on 2007-07-16
I have Ububtu 7.04 installed and I have Beryl running nicely BUT I whenever I reboot my machine /usr/lib/libGL.so has been removed! This stops me building my Irrlicht project (can't find -lGL when linking).

I can recreate the link to /usr/lib/libGL.so.1 manually and its all fine again, the game links and runs ok. Its not quite as fast as I'd expect though so I guess its doing it via software.

Can anyone tell me why libGL.so keeps being removed and what I should to to make it use the right version?

------------
   Allan

---

### Post by jasonlfunk on 2007-07-16
Everytime you reboot the file is deleted?

---

### Post by amoore on 2007-07-16
try

```
sudo ln -s /usr/lib/libGLU.so.1.3.060501 /usr/lib/libGLU.so
```

---

### Post by allan175 on 2007-07-17
Yes, everytime I reboot it has gone again.

I manually recreate it everytime it goes missing (its libGL.so) and everything is ok.

I just wanted to know how to stop it being deleted in the first place. And, whether or not its the right one I'm using (software/hardware) since the game I am working on is not running as smoothly as I'd expect considering its just blitting a few sprites.

---

