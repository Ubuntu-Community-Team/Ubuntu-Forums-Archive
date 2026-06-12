---
title: "Best way to get playtime / runtime / length from a media (at least mp3)  file?"
date: 2008-05-09
forum: General Help
---

### Post by olejorgen on 2008-05-09
Currently I'm using mplayer:
```

mplayer -identify -frames 0 *mp3 | grep ID_LENGTH

```
but it's kinda slow.

---

### Post by Monicker on 2008-05-10
You could try mp3info.

---

### Post by olejorgen on 2008-05-10
Sweet, It would be more convenient with a tool that supported more formats though

---

