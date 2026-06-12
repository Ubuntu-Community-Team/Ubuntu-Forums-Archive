---
title: "Trying to get back to Dekstop"
date: 2008-05-07
forum: General Help
---

### Post by CHUNKYBOWSER on 2008-05-07
I go to the place to turn of the X Server (ctrl+alt+F1?) and I turn off the X Server successfully so I can install my video driver. But when I try to go back (ctrl+alt+F7) it just brings up a black screen with a blinking cursor and it never brings me back to the desktop. So, I have to restart and the X Server is back on. Help! D:

---

### Post by nick_h on 2008-05-07
Try:
```
sudo /etc/init.d/gdm start
```

---

