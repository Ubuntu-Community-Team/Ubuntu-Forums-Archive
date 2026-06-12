---
title: "This is a beryl question."
date: 2007-04-21
forum: General Help
---

### Post by Madmoose on 2007-04-21
Everything seems to be working but two things:

1) Can anyone tell me why one the first side of the cube everything us working perfectly, but if I move to any of the other three sides nothing works right? The background/ desktop is black, and the windows multiply when you move them if you know what I mean. Only the one side works. 

2) The 3D Effects on the cube don't work, so it's just a flat cube. 


Any info and fixes would be nice. 

Thanks, 

Moose

---

### Post by Ziox on 2007-04-21
do you have direct rendering enabled?

glxinfo | grep direct

---

### Post by Madmoose on 2007-04-22
> **Ziox said:**
> do you have direct rendering enabled?

glxinfo | grep direct


```
madmoose@madmoose-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

---

