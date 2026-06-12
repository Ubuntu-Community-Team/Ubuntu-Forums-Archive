---
title: "I want to do get output for what/how many windows are open in a desktop."
date: 2013-05-08
forum: General Help
---

### Post by baillou2 on 2013-05-08
How can I do this? 

In other words, I open a terminal and do "whatever" to read what applications have active windows in the DE.

Anyone have any ideas?

---

### Post by steeldriver on 2013-05-08
well it's a bit oldschool, I don't know if there's a more modern alternative (perhaps via dmesg?) but

```
xwininfo -root -children
```
or
```
xwininfo -root -tree
```

should have that information

---

### Post by baillou2 on 2013-05-09
I'll check it out. 
Thanks.

---

### Post by Cheesemill on 2013-05-09
```
wmctrl -l
```
You may need to install the wmctrl package first.

---

