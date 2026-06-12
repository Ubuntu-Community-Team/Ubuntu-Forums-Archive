---
title: "usplash dont work at shutdown"
date: 2007-11-04
forum: General Help
---

### Post by artir on 2007-11-04
When I shutdown my laptop I cannnot see the orange bar. Instead I see a black screen with this "_" simbol blinking; then it turns off normally.
My /etc/usplash.conf is set to x=1024 y=768, my screen resolution. I have tried to sudo dpkg-reconfigure usplash and update alternatives, but i havent managed to get it working.
Some ideas?

---

### Post by yostral on 2007-11-04
It sometimes does the same here. I reinstall the usplash package and it works.

---

### Post by por100pre1 on 2007-11-04
Try using Startup Manager to setup usplash:

```
sudo aptitude install startupmanager
```

---

