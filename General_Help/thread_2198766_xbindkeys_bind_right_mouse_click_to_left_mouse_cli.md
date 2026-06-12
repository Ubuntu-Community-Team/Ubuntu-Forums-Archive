---
title: "xbindkeys bind right mouse click to left mouse click"
date: 2014-01-10
forum: General Help
---

### Post by yarlaz on 2014-01-10
Hello, i am trying to simulate a right mouse click when the left mouse click is pressed.
The only way i managed to make this work is by adding a *sleep* command before the actual *mouseclick*
```
# bind right mouse click to left mouse click
"sleep 0.2 && xte 'mouseclick 3 &'"
  m:0x10 + b:1
```
without the initial sleep command it does not work. I would like to be able to achieve the same result but without having to use that initial delay... do you have any hint on how could i achieve such result?
Thank you for your help

---

### Post by yarlaz on 2014-01-12
nobody? any hint?

---

