---
title: "no sound"
date: 2005-06-09
forum: General Help
---

### Post by D_C on 2005-06-09
Hey, im pretty new to linux, but i managed to get ati drivers etc, installed and i wanted to play some games, but i have no sound at all in games. Im using a USB headset, sound works fine in XMMS, ive also noticed i dont get any sound viewing flash files either. Can anyone help me ived asked alot of people if they know what i can do to fix this but it seems no one knows the answer. I have alsamixer all turned up aswell. Thanks.

---

### Post by sethmahoney on 2005-06-09
Are you trying to play native Linux games, or Windows games through Cedega?

If its native Linux games, I don't have any advice to offer, but if its through Cedega, opening up a terminal and typing

```
killall esd
```

before you play should get sound going.

---

