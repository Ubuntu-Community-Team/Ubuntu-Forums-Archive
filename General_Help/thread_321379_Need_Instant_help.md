---
title: "Need Instant help"
date: 2006-12-18
forum: General Help
---

### Post by Siberianfox272 on 2006-12-18
i installed compiz and now need to adjust color depth to 24. how do i do this?

---

### Post by aysiu on 2006-12-19
I don't know much about Compiz, but I think you can adjust the color depth by editing the /etc/X11/xorg.conf file: ```
sudo nano -B /etc/X11/xorg.conf
``` Scroll down to the "Screen" section and you'll see the default color depth.

---

### Post by Henry Rayker on 2006-12-19
One general suggestion: It might be beneficial to do two things differently about the way you title your threads. First, don't demand help (using words like immediately, now, require etc) and Second, make your thread titles more informative (an example for this could be, "Compiz in 24 color depth. How?"

---

### Post by bodhi.zazen on 2006-12-19
Best source of instant help is the man pages or google :p

```
sudo vim /etc/X11/xorg.conf
```

Change to>  DefalutDepth 24

---

