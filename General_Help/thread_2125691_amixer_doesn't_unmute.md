---
title: "amixer doesn't unmute"
date: 2013-03-14
forum: General Help
---

### Post by ubunet on 2013-03-14
My Xubuntu 12.10 x32 have this shortcuts for Fn multimedia keys:

```
amixer -c 1 sset Master playback 5%+
amixer -c 1 sset Master playback 5%-
amixer -c 1 sset Master playback toggle
```

Only the toggle doesn't unmute. I need to unmute in GUI.

---

### Post by ubunet on 2013-03-14
Adding ***-D pulse*** parameter works to me.
```
amixer -c 1 -D pulse sset Master playback toggle
```

---

