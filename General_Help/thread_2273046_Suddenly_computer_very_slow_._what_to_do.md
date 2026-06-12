---
title: "Suddenly computer very slow . what to do?"
date: 2015-04-10
forum: General Help
---

### Post by 171742 on 2015-04-10
Hello,

pretty much that. I got ubuntu 14.4 lts and did not change anything. From this morning on its very slow. What to do?

I am VERY noob, so please easy.

Thanks!

---

### Post by dino99 on 2015-04-10
when something comes badly, the first thing you may think of is glancing to the logs: xorg.0.log inside /home, and /var/log/*
you should find some usefull warnings/errors to work with

---

### Post by tgalati4 on 2015-04-10
Check your hard disk light.  If it is on continuously, then perhaps you have run out of RAM and you are now using swap.  Open a terminal (when you can--be patient):

```
free
```

Don't shut down the computer, but let it finish whatever it is doing.

---

