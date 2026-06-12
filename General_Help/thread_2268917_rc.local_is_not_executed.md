---
title: "rc.local is not executed"
date: 2015-03-12
forum: General Help
---

### Post by ben147 on 2015-03-12
Hey zirka, I have a question. In 14.04 I used a skript to be executed in rc.local on startup, to make ARandR load a setup with 2 monitors:

/bin/sleep 10  && /bin/bash /home/ben/Dokumente/2monitore.sh

Do you have an explanation why exact the same skript is not executed via rc.local on startup in 14.10?

---

### Post by zika on 2015-03-12
I would try```
([COLOR=#000000]/bin/sleep 10;/bin/bash /home/ben/Dokumente/2monitore.sh)&
```[/COLOR]

---

