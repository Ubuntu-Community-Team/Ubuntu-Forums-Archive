---
title: "3d Games run slow on high-end vidcard"
date: 2007-05-19
forum: General Help
---

### Post by tb87670 on 2007-05-19
I am having problems with my GeForce 6800 vidcard. 3d games run pretty slow for the card installed (in M$ Windows ImOnCraXP I could run any new game) and simple 3d games are running at the pace to where I can count the frames. I turned on X and I am wondering if there is anything else I need to do. Thanks in advance.

---

### Post by jtraub on 2007-05-19
Please, open terminal and exec
```
glxinfo | grep rendering
```

I guess, it will output direct rendering: no

Have you installed appropriate video drivers?

If yes, try to measure rendering speed with
```
glxgears
```

---

