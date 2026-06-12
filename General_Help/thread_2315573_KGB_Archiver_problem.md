---
title: "KGB Archiver problem"
date: 2016-02-29
forum: General Help
---

### Post by Vuzee01 on 2016-02-29
Hi guys, on my VPS i have installed ubuntu 15.04 and i installed kgb archiver, and when i try to compress file like```
kgb -9 file.kgb myfile.example
```

afther few second i get output Killed, and when i try to compress without -9 parameter it goes well...

So what is problem?

[IMG]http://i.imgur.com/uHHVO8G.png[/IMG]

---

### Post by Vuzee01 on 2016-02-29
Okay, i found out what is problem, my vps only has 1gb ram and this -9 compression needs to have atleas 1.6gb ram...

---

