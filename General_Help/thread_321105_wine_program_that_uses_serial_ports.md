---
title: "wine program that uses serial ports"
date: 2006-12-18
forum: General Help
---

### Post by earobinson on 2006-12-18
I have a windows program that tries to use com1 is there any special setup that I need to get wine to use tty1 (which I assume is com1)

currently the program fails when it tries to talk to com1

---

### Post by jsandys on 2006-12-19
I think that tty1 is com2, tty port numbers are zero based and com port numbers are one based.

---

### Post by earobinson on 2006-12-19
lol wow that was dumb of me, thanks!

---

