---
title: "Graphics, Moving Windows and Video is very chopyy"
date: 2008-05-20
forum: General Help
---

### Post by dud808 on 2008-05-20
Hi all, I'm having trouble with the new Ubuntu 8.04, I have a core 2 duo processor with 2Gb of ram and a Nvidia 7600GS PCI-Ex and I do use the restricted drivers.

My problem is when I move windows around on the screen the window edges all break up and its not smooth at all, come to think of it my whole ubuntu experience is not too smooth, also videos such as DVD's and Xvid have lines shooting through especially during fast scenes, I very much want to stay on Ubuntu but I'm forced to boot back into Vista to watch videos (even on youtube).

Would greatly appreciate any help

Thanks

---

### Post by eldragon on 2008-05-20
got compiz running? my guess is you dont.


do 
```

glxinfo | grep direct

```

should read: direct rendering: yes

otherwise, youve got a display driver issue. search the wiki on how to install nvidia restricted drivers.

all i can think of.

---

### Post by bobjenkins on 2008-05-20
I had this same problem only with an ATI card, it was a driver issue. I had two different drivers installed (noob) so I had to uninstall one, I kept the restricted driver and it works great.

---

### Post by HunterCyprus on 2008-05-20
I have an ATI X850 and I am using only the restricted drivers.  I am having an issue with 3D accelerated applications flashing.  Only way I can get past this is to run (only tested on one game, Dominions 3) the game in full screen at my desktop resolution.  I have to reset this each time I load the game.

Any ideas?

PS. I did check the Direct Rendering
PPS.  I am running Compiz

---

