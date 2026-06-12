---
title: "Steam Games ALL malfunction after upgrade to 19.10"
date: 2019-11-07
forum: General Help
---

### Post by Hasimir on 2019-11-07
After upgrading my system from 19.04 to 19.10 all my Steam games (both previously running and freshly installed) have graphical malfunctions.
I have tested them in Ubuntu and Ubuntu Wayland.
I have tested them with Xorg and nVidia.
Every time the games either fail to launch, or start but fail to render on screen (i hear the sound in the background, everything is present and working... just... invisible to me).

What is happening?

---

### Post by tux-peng on 2019-11-07
What exact card?  Binary drivers or just mesa?  Can you run glxgears?  Output of ```
glxinfo | grep -i opengl
```?

---

