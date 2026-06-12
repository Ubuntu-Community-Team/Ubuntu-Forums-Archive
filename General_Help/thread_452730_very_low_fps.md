---
title: "very low fps"
date: 2007-05-23
forum: General Help
---

### Post by Loukisgr on 2007-05-23
hi everyone,

i am new to this forum (and to linux) so i'd like to ask something that i hope isn't very rediculus.

When i try to play a game i can see that either the mouse disappears or the game is running slow. What i found is that the fps is very low (1,5 fps!!!! using 640X480 resolution). I have already install ati catalist(it doesen't give many option to change). I have an X1600 XT which is quite fast. What else can i do?? Does it have with the resolution tha i have on desktop?(1280X1024)
 thanks in advance

---

### Post by codesplice on 2007-05-23
Hi **Loukisgr**,
My first guess would be wondering if you have 3d acceleration enabled.

Try ```
glxinfo | grep direct
``` in a terminal.  

You want it to say yes:
```
csplice@Lappy486:~$ glxinfo | grep direct
direct rendering: Yes

```

If not, you might need to look into how to enabled 3d acceleration on your card.

Hope this helps get you started in the right direction.

---

### Post by Loukisgr on 2007-05-24
Thank you very much!! it was no enabled.. I will searth the web to find how

---

