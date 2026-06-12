---
title: "Xmodmap remove lock = Caps_Lock doesn't work"
date: 2012-11-29
forum: General Help
---

### Post by Zvlwab on 2012-11-29
my Xmodmap file looks like this.
```
$ cat /etc/X11/Xmodmap 
remove lock = Caps_Lock
keycode 66 = BackSpace
```

It should remove caps lock as caps lock and set it as an alternative backspace. Setting it as backspace does work, but removing it as a lock doesn't anymore.
It has always worked for me, and it still works on my laptop. But since I last reinstalled my pc it doesn't work there anymore. I'm running Xubuntu 12.04.

---

