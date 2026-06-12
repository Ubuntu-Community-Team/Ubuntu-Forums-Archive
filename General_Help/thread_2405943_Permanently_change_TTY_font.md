---
title: "Permanently change TTY font"
date: 2018-11-13
forum: General Help
---

### Post by Matyy on 2018-11-13
Hi,

I want to change my TTY fonts.
Ubuntu 18.10

it works wit setfont:
```
setfont ter-powerline-v32n.psf.gz
```

I changed my /etc/default/console-setup to:
```
ACTIVE_CONSOLES="/dev/tty[1-4]"  
CHARMAP="UTF-8" 
FONT="ter-powerline-v32b.psf.gz"
```

But setupcon just shows: "putfont kdfontop invalid argument". Adding the full path doesn't help.
I also still have 6 TTYs, not 4.
It seems this file isn't parsed at all.

dpkg-reconfigure console-setup has no effects whatsoever, and there I am using preinstalled fonts. It changes the console-setup file, tho.


Any ideas how to fix this? The font obviously works.

---

