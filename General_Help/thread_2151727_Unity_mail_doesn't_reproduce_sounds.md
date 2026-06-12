---
title: "Unity mail doesn't reproduce sounds"
date: 2013-06-05
forum: General Help
---

### Post by tigerjack89 on 2013-06-05
Hey there.
As the title says, unity mail doesn't reproduce any sound when I receive a new mail.
Of course, I setted different audio files to test this, but I have always the same problems.

---

### Post by kostkon on 2013-06-05
unity-mail seems to be using libcanberra to play sounds, i.e. the system sounds infrastructure of ubuntu; thus, open your sound preferences and check the volume level for system sounds.

---

### Post by tigerjack89 on 2013-06-05
> **kostkon said:**
> unity-mail seems to be using libcanberra to play sounds, i.e. the system sounds infrastructure of ubuntu; thus, open your sound preferences and check the volume level for system sounds.
solved. I don't know why but the alert volum was settedto 0 :S

thanks :)

---

