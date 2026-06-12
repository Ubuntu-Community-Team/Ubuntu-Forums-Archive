---
title: "Graphics Fuzzy"
date: 2006-10-27
forum: General Help
---

### Post by JPMaximilian on 2006-10-27
I had installed compiz and all that jazz, but decided that the resources requird for the eye candy weren't worth it.  So i'm not running compiz or any other those fancy graphics things anymore, but I think I messed up my xorg.conf or something.  Sometimes panel icons will get distorted and cut up and when I drag icons, they do a similar thing.  Does anyone know how to reserve these effects?  Thanks.

---

### Post by ~LoKe on 2006-10-27
Either restore your backup, or type this in your terminal:

```
sudo cp /etc/X11/xorg.conf_back && sudo dpkg-reconfigure xserver-xorg
```

The first bit isn't necessary, because the reconfigure should backup for you, but I like to know what my stuff is named.

---

### Post by JPMaximilian on 2006-10-28
Thanks ~Loke, that command didn't work exactly, but when I just ran

sudo dpkg-reconfigure xserver-xorg 

that fixed the problem.

---

### Post by ~LoKe on 2006-10-28
The first part was simply to make a back up. ;)

---

### Post by JPMaximilian on 2006-10-29
Can you do two commands on the same line by using &&

?

---

### Post by ~LoKe on 2006-10-29
> **JPMaximilian said:**
> Can you do two commands on the same line by using &&

?

Sort of.  Using && would mean "once the first command completes, do the next".

So, the second one wouldn't occur until after the first one finishes.

---

