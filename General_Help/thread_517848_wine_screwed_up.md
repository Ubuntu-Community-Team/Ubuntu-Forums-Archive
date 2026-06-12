---
title: "wine screwed up"
date: 2007-08-05
forum: General Help
---

### Post by -grubby on 2007-08-05
I was installing wine and accidentally pressed enter when it was installing so it quit halfway through. I can no longer access the add/remove applications panel it exits after saying dependency generation. I want to know how to get rid of wine so I can install it again

---

### Post by -grubby on 2007-08-05
by the way I use Ubuntu 7.04

---

### Post by avik on 2007-08-05
Try typing this in the terminal:

```
sudo apt-get remove --purge wine
```

Enter your password and press enter.

---

### Post by -grubby on 2007-08-05
I tried above and it says


Reading package lists... Done
Segmentation fault (core dumped)

---

