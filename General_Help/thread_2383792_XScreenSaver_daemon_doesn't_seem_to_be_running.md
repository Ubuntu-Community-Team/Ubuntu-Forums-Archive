---
title: "XScreenSaver daemon doesn't seem to be running"
date: 2018-01-29
forum: General Help
---

### Post by raleigh3 on 2018-01-29
Yesterday, Xscreensaver was working.

Now it says

```
The XScreenSaver daemon doesn't seem to be running on display ":0".  Launch it now?
```

---

### Post by Dennis N on 2018-01-29
That's usually because xscreensaver has not been added to startup applications. It's not automatic and has to be added by you. Ubuntu MATE 16.04 might have mate-screensaver installed instead by default - Ubuntu MATE 17.10 does. If so, and you want to use xscreensaver instead, you should disable mate-screensaver from startup applications. Command for xscreensaver in startup applications is **xscreensaver -no-splash**

---

### Post by raleigh3 on 2018-01-29
Thanks. Now it's working.

---

