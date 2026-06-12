---
title: "speakers work strangely"
date: 2008-05-26
forum: General Help
---

### Post by Meow27 on 2008-05-26
ive had sound problems using ubuntu for a while. i would usually have to jack the sound up alot in order to get a somewhat good volume (in comparison to windows)
so this morning, i decided to unplug one of my speakers (1 speaker is directly connected to the main.)

it turned out that the main speaker was barely producing any noise at max volume and the other speaker was the one really doing the work

anyone know any fix for this?

thanks in advance

oh and if this helps
```
cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 16

```

---

### Post by Meow27 on 2008-05-27
bump

---

### Post by inportb on 2008-05-27
What if you try a different pair of speakers? Perhaps your two speakers developed differences, thus making the output unbalanced.

---

### Post by Meow27 on 2008-05-27
mmmm not sure if that will work.... but ill try.. as i said. when i use a different os, this problem doesn't emerge...

---

### Post by Meow27 on 2008-05-31
ok i think i fixed the problem,

using Wine to run winamp, i noticed that all of the volume was being sent to the left speaker, i switched it back to normal, still lower volume than windows, but its always been like that..

thanks anyway

---

