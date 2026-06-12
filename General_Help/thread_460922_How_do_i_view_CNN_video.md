---
title: "How do i view CNN video?"
date: 2007-06-01
forum: General Help
---

### Post by steve196 on 2007-06-01
mplayer firefox plugin is installed, but for some reason firefox still uses the useless totem player. How can i make it use mplayer or anything else, that actually works?
Thanks!

---

### Post by Blender on 2007-06-01
How about:
```

[~] $ sudo apt-get remove totem-mozilla
[~] $ sudo apt-get install mozilla-mplayer

```
?

Be careful, as there might be something depending on **totem-mozilla**.

---

### Post by bluefly on 2007-06-03
Thanks Blender, that worked for me.  (Ubuntu 7.04)

---

