---
title: "play .wav doesn't work"
date: 2007-01-25
forum: General Help
---

### Post by jmvidalvia on 2007-01-25
I want to play a system sound form terminal, but it seems play command is not in the system:
play /usr/share/sounds/*.wav
bash: play: command not found

¿?
Thanks a lot!

---

### Post by guysmiley25 on 2007-01-25
try 

```
aplay example.wav
```

---

### Post by jmvidalvia on 2007-01-25
Works!
Thank you!

---

### Post by guysmiley25 on 2007-01-25
No worries. It took me ages to figure that one else as well :)

---

