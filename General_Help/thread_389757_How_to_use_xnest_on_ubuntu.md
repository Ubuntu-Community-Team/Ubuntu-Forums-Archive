---
title: "How to use xnest on ubuntu ?"
date: 2007-03-21
forum: General Help
---

### Post by sdil on 2007-03-21
Can anyone donate your idea about how to use XNEST on ubuntu 6.10 :confused:

---

### Post by Ramses de Norre on 2007-03-21
This should get you started:
```
sudo aptitude install xnest
Xnest :1 -ac &
export DISPLAY=:1
```
Now you can start programs from the terminal you executed these commands from or use that terminal to launch a window manager and continue from there.

---

