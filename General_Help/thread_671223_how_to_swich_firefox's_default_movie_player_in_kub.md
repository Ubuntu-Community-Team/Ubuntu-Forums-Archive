---
title: "how to swich firefox's default movie player in kubuntu?"
date: 2008-01-18
forum: General Help
---

### Post by zivxx on 2008-01-18
Hi everybody,
I've installed the mplayer instead of kaffiene in kubuntu and i want to make it my default player of firefox, i already made it as my default player on the system but not on firefox.

anyone knows how to do this?

---

### Post by ThrobbingBrain66 on 2008-01-18
You'll need to uninstall the kaffeine-mozilla package.  You'll also need to install the mozilla-mplayer package if you haven't done so.

```
sudo apt-get remove --purge kaffeine-mozilla
sudo apt-get install mozilla-mplayer
```

---

### Post by zivxx on 2008-01-18
thanks dude it worked

---

