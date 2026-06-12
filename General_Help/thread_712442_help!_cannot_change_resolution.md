---
title: "help! cannot change resolution"
date: 2008-03-01
forum: General Help
---

### Post by xMikeL on 2008-03-01
hello.

i had problems before with my graphics driver. then i finally got it to work

but, i restarted the computer and it came up with something like safe mode

because of a driver (sorry i kinda forget). Now i cant change my monitors res,

its stuck at 640x480. when i go to the option of changing it

it doesnt have any other resolution

but i can still do the wobbly things with the windows.

I tried a few things but nothing worked.

---

### Post by LuisGMarine on 2008-03-01
Funny I just ran into the same problem not too long ago, run this and make sure you pick your resolution when it asks you for it.

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xMikeL on 2008-03-01
i set a few options and nothing changed. i think it crashed and came up with this

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080302101223

**EDIT:** okay somehow it magically fixed itself, but:

u know on a window how u have the title bar?

well thats really really small

text unreadable

---

