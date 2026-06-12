---
title: "Need help fixing buttons"
date: 2007-06-14
forum: General Help
---

### Post by jellomonk on 2007-06-14
Please look at my SS and tell me what I can do to fix the banding on my buttons. Thanks in advance.

---

### Post by tpg on 2007-06-14
What graphics card do you have, and what driver are you using? I think that could be the problem. Also, is the banding static, or does it move/flicker if you move the mouse over it, or move the containing window?

---

### Post by jellomonk on 2007-06-15
I'm using a Radeon Mobility 7500 M7, I'm not really sure what drivers I'm using. And once I roll over the buttons with my mouse they clear up and look normal.

---

### Post by jellomonk on 2007-06-16
bump

---

### Post by strabes on 2007-06-16
duplicate post, oops.

---

### Post by strabes on 2007-06-16
paste the output of this command: ```
fglrxinfo
```

If it looks something like this:> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

then you need to follow [this ](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3)guide.

If the part for feisty doesn't work, follow the part for edgy.

---

