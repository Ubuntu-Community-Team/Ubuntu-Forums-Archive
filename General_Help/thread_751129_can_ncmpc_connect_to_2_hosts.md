---
title: "can ncmpc connect to 2 hosts ?"
date: 2008-04-10
forum: General Help
---

### Post by sujoy on 2008-04-10
i have mpd set up on my laptop as well my desktop.

while everything works fine i would like ncmpc to connect to both the machines and show me the contents of both the mpd database.

is this possible and if yes then how?

---

### Post by mcduck on 2008-04-10
Not at once, but you could just start two ncmpc's, each with connecting to their own host.

```
ncmpc --host=HOSTNAME
```

Sonata allows you to select between different hosts from a GUI menu, but even then it can only be connected to one host at a time.

---

### Post by sujoy on 2008-04-10
yes i know about that option,

well guess i have to do with 2 ncmpc till they come out with a multiple host option

---

