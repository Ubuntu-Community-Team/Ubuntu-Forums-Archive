---
title: "x11vnc Screen Black at Login"
date: 2016-08-06
forum: General Help
---

### Post by theonlytalkinggoat on 2016-08-06
I have ssh access to an Ubuntu 16.04 box and I am normally able to connect, via x11vnc, using -display :0 -connect [server.tld]. It isn't a headless system and this only seems to work, when there is someone logged in. When the machine is at the login screen, however, the vnc screen is black, with a cursor. I have tried 
```


    sudo x11vnc -auth /var/run/lightdm/root/:0 -display :0 -forever 
    -bg -connect [server.tld]

```

but it doesn't make a difference. The screen is still black, with a cursor. How do I connect, from the login screen?

---

### Post by theonlytalkinggoat on 2016-08-09
Bump

---

