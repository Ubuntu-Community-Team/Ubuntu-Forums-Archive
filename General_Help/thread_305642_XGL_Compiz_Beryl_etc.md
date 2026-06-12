---
title: "XGL Compiz Beryl etc"
date: 2006-11-23
forum: General Help
---

### Post by yosef on 2006-11-23
I am running a k/xubuntu on dell inspiron b120 how can I tell if I can do a 3d desktop?

---

### Post by groggyboy on 2006-11-23
```
glxinfo | grep render
```

if it returns "direct rendering: Yes" then you are good to go.

---

### Post by xpod on 2006-11-23
[ATTACH]19883[/ATTACH]


Strange???
Seems i cant run beryl as i dont have no direct rendering  apparently.

It used to say "yes".
Ach well,not to worry:rolleyes: 

Good luck yosef

---

### Post by yosef on 2006-11-23
yosef@rlyeh ~> glxinfo | grep render
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225


YAY!!!!  Thanks! (but what is the libGL warning all about?)

---

### Post by groggyboy on 2006-11-23
yosef: i get a similar libGL error - i ignore it because it hasn't caused me any issues! ;) be sure you use the proper instructions for your video card (ie ATI/nVidia/Intel, etc)

xpod: if you are running beryl when you try to check for direct rendering, it'll say No.  it has something to do with xgl/aiglx taking over direct rendering and not letting other apps use it.  mine does the same thing.  If you turn off beryl and try again, it should say Yes.

---

### Post by xpod on 2006-11-23
Learn something new everday m8:D

---

### Post by PriceChild on 2006-11-23
> **groggyboy said:**
> xpod: if you are running beryl when you try to check for direct rendering, it'll say No.  it has something to do with xgl/aiglx taking over direct rendering and not letting other apps use it.  mine does the same thing.  If you turn off beryl and try again, it should say Yes.That's just with xgl, not aiglx.

---

### Post by yosef on 2006-11-23
I am now running beryl-aiglx and it is fine under kde but whu wont it work on xubuntu?

---

