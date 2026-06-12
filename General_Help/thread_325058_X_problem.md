---
title: "X problem"
date: 2006-12-24
forum: General Help
---

### Post by nosco on 2006-12-24
Hi, I am having a problem with X at boot up on a fresh 6.10 install. I followed the install guide and got the latest nvidia driver, but now I get an X error on startup and the splash screen will not load. In order to get to the desktop, I login from the command line and type "startx" and it seems to work. What do I need to configure to have X load without having to type "startx" every time?

Thanks in advance.

---

### Post by dbbolton on 2006-12-25
maybe you need to add startx to your init scripts...

---

### Post by nosco on 2006-12-25
Here is an update of the error message I get.

GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel slx:pbuffer -accel xv:fb0 -auth /var/lib/sdm/ :0.Xauth -nolisten tcp vt9

Note: that is pretty close to exact, may be an extra or missing space in there somewhere :)


Thanks in advance.

---

### Post by nosco on 2006-12-26
Anyone have any suggestions I could try? I've searched other posts, tried some things.. But problem still exists :(


Thanks.

---

