---
title: "libEGL.so.1: undefined symbol"
date: 2017-12-02
forum: General Help
---

### Post by manisabri on 2017-12-02
Hi,

I'm unable to use Unity and run VLC and mplayer after an update last week. They give me the below error:

symbol lookup error: /usr/lib/x86_64-linux-gnu/mesa-egl/libEGL.so.1: undefined symbol: drmGetDevice2

Any ideas? 

Thank you,
Mani

PS I'm using 16.04 64bit on an Intel I7 laptop with no dedicated graphic card.

---

### Post by Perfect Storm on 2017-12-02
Thread Moved to General forum.

---

### Post by mc4man on 2017-12-02
run this & post results
```
apt policy libegl1-mesa
```

---

