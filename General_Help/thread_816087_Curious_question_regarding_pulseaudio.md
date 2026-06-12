---
title: "Curious question regarding pulseaudio"
date: 2008-06-02
forum: General Help
---

### Post by R3VAMP3D on 2008-06-02
Would blacklisting pcspkr on a laptop result in absolute loss of audio?

---

### Post by sdennie on 2008-06-02
Probably not.  Your audio driver is probably completely unrelated to that module.  See the following for more info on what audio driver you are using:

```

lsmod | grep snd

```

---

### Post by R3VAMP3D on 2008-06-02
Yeah I snooped around and finally gave up and put Gusty back on it. Seems to have fixed it. Now ive got the itchy syndrome that I want hardy back on it but if the audio is going to blow out again, I don't think I want to.

---

