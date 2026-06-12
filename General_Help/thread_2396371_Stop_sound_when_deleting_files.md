---
title: "Stop sound when deleting files"
date: 2018-07-14
forum: General Help
---

### Post by raleigh3 on 2018-07-14
Using Ubuntu Mate 18.04.

I have set the "Sound theme" to "No sounds", yet I still hear those irritating sound when deleting files.

Any fix?

---

### Post by raleigh3 on 2018-07-14
Open dconf-editor. Browse to
org/gnome/desktop/sound
On the right, unclick event-sounds.

Edit

It did NOT work.

---

### Post by raleigh3 on 2018-07-15
I found an answer.

```
Sound Preferences 

  Set alert volume to mute.
```

---

