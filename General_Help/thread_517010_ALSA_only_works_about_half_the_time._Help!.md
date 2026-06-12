---
title: "ALSA only works about half the time. Help!"
date: 2007-08-03
forum: General Help
---

### Post by Sparky222B on 2007-08-03
I can't explain it! About half the times I boot Ubuntu, ALSA works perfectly, no problems. But the other half, ALSA outputs nothing and any application attempting to play audio via ALSA just freezes and I have to xkill it.

---

### Post by be4truth on 2007-08-04
I had that happening a couple of times with a very cheap onboard sound card. You could use OSS if that works better.

Try this in a terminal:

```
sudo dpkg-reconfigure alsa-base 
```

or this if the above doesn't work:

```
sudo dpkg-reconfigure linux-sound-base
```

---

### Post by Sparky222B on 2007-08-04
OSS sucks, though, it doesn't play ogg..

---

### Post by Sparky222B on 2007-08-04
I'll try that tonight and let you know how it works. THanks.

---

