---
title: "Wubi XServer Error"
date: 2007-05-26
forum: General Help
---

### Post by Eminem on 2007-05-26
Is there a way to install Wubi with the ability of being able to chose your resolution and graphics card like in a real alternate installation? Last time I installed Wubi I got a X-Sever error regarding my Graphics Card which is ATI; but when I installed Ubuntu on a partition a while ago via alternate installation, I was able to chose my screen resolution and graphics card and it worked great.

The question is, is there a way to install Wubi with the ability of being able to chose your resolution and graphics card like in a real alternate installation?

---

### Post by varchar255 on 2007-05-26
Are you able to get to the Ubuntu login screen? If so, I believe you can choose a failsafe terminal session, then log in and run the command:

```
sudo dpkg-reconfigure xserver-xorg
```

and it should allow you to choose those options.

---

### Post by Eminem on 2007-05-27
> **varchar255 said:**
> Are you able to get to the Ubuntu login screen? 

Nope.

---

### Post by tuxcantfly on 2007-05-28
Ctrl-Alt-F1 or Ctrl-Alt-F2 should do the trick with getting logged in...

---

